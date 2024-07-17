17 juillet 2024, Adrien Gahery

Ce document est issu d'un book que l'on m'a demandé. Il donne également un aperçu de ma façon de travailler.

## Requête SQL

La requête ci-après mobilise un grand nombre de concepts techniques (windowing, CTE) ainsi que de modélisation de données (agrégats, sélection par localisation).

On se propose de calculer la densité moyenne (habitant par kilomètre carré) de chacune des routes intercommunales du département de l'Hérault. J'ai importé les données de la BD Topo de l'Institut Géographique National et Forestier (IGN) dans une base de donnée locale.

### Processus

```nomnoml
[<state>Densité de population par commune x 1 000 000 (km²)] -> Produit cartésien[<state> Chaque occurrence de route intercommunale pour chaque commune desservie]
[<state>Nombre de communes irriguées par route intercommunale] fonction de Windowing -> [Chaque occurrence de route intercommunale pour chaque commune desservie]
[<state> Chaque occurrence de route intercommunale pour chaque commune desservie] Aggrégat -> [<state> Somme des densités divisée par le nombre de communes desservies]
```

- On fait les comptages par table et le calcul de surface avant d'opérer le produit cartésien
- On minimise le nombre de rangs dans le produit cartésien par une condition spatiale
- On profite que la moyenne des densités est la densité globale des éléments auxquels correspondent la moyenne pour effectuer ce calcul lors de l'agrégat selon les lignes de bus


### Code SQL

```sql
/* densité moyenne de population desservie par les routes intercommunales de la BD Ortho
Decembre 2023, Adrien Gahéry */

--DROP TABLE IF EXISTS public.tryout_1;

WITH commune AS (SELECT id, nom, insee_com, (population/st_area(geom))*1000000 AS densite, geom FROM public.commune),
     route AS (SELECT DISTINCT COUNT(c.insee_com) OVER (PARTITION BY r.numero) AS nbre_commune_traverse, r.numero, r.geom
                    FROM public.commune AS c, public.route as r
                    WHERE type_route = 'Route intercommunale'
                        AND c.geom && r.geom
                        AND ST_Intersects(c.geom, r.geom)
                    ORDER BY r.numero                ),
     cartesian AS (SELECT ROW_NUMBER() OVER(ORDER BY route.numero) AS id, route.numero, route.nbre_commune_traverse, commune.nom, commune.insee_com, commune.densite
                    FROM route, commune
                    WHERE commune.geom && route.geom
                        AND ST_Intersects(commune.geom, route.geom))
SELECT c.numero, sum(c.densite)/c.nbre_commune_traverse AS densite_moy --, r.geom
    --INTO public.tryout_1
    FROM cartesian AS c--, route AS r
    --WHERE c.numero = r.numero
    GROUP BY c.numero, c.nbre_commune_traverse--, r.geom
    ;
```

- Dans la *Common Table Expression* (CTE) nommée cartesian, on utilise une fonction de Windowing qu'on nomme id. Cela créée un index. La requête ne marche pas si on l'omet. Syntaxe initialement trouvée pour donner un index aux vues PostGIS; le client QGIS ne les affiche pas sinon.
- Quelques fin de lignes sont désactivées dans la requête principale. Si on enlève les ``` -- ``` marqueurs de *user input*, on obtient adjoint au résultat non géométrique la géométrie des routes (réutilisation de la CTE), et on l'enregistre sous le nom public.tryout_1.
- Je mets par habitude la commande *DROP TABLE IF EXISTS* dès que je créée une table.
- la condition *commune.geom && route.geom* a pour but d'optimiser le temps de calcul en comparant d'abord les emprises des géométries avant de conduire le *ST_Intersects*, plus gourmand en ressources. Il semble que l'optimisation des scripts soit moins probante lorsqu'on exécute le SQL *via* SQL Alchemy dans un Jupyter Notebook, sujet que nous allons détailler dans la section suivante.

## Résultats

### Requête non géographique 

![Alt text](images/Screenshot/240717_2_postgres.png)
*Affichage direct dans Microsoft Vs Code*

### Requête avec colonne géographique

![Alt text](images/Screenshot/240717_3_postgres.png)
*Il n'y a pas d'affiche des données directement dans VS Code*

![Alt text](images/Screenshot/240717_4_QGIS.png)
*On se connecte à la base de données dans QGIS par ***Ctrl+Shift+D***

![Alt text](images/Screenshot/240717_6_QGIS.png)
*Les données ainsi que la table attributaire dans QGIS*

