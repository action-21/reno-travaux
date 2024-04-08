# @renolab/base-travaux

Un open data des travaux de rénovation énergétique de l'habitat.

## ⚙️ Méthodologie

#### Catégorisation des travaux de rénovation énergétique

La littérature utilise majoritairement la notion de **postes de travaux** pour catégoriser les travaux de rénovation énergétique. On retrouve également cette notion dans le [Code de la construction et de l'habitation](https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000043976954) pour définir une rénovation performante:

> **b du 17° bis de l'article L111-1**
>
>L'étude des six postes de travaux de rénovation énergétique suivants : l'isolation des murs, l'isolation des planchers bas, l'isolation de la toiture, le remplacement des menuiseries extérieures, la ventilation, la production de chauffage et d'eau chaude sanitaire ainsi que les interfaces associées.

En croisant cette base de travail avec les répertoires de travaux identifiées, une première arborescence de travaux a été réalisée.

- Chauffage et eau chaude sanitaire
    - Chaudières
    - Chauffe-eaux
    - Émetteurs
    - Poêles et inserts
    - Pompes à chaleur
    - Réseaux de chaleur
    - Systèmes solaires
- Isolation des combles et toitures
- Isolation des murs
- Isolation des planchers
- Ouvrants
- Protections solaires
- Refroidissement
    - Climatiseur
    - Raccordement à un réseau de froid
- Régulation
- Réseau
- Ventilation

#### Codification des catégories de travaux

Inspirée de [publicodes](https://github.com/publicodes/publicodes), la codification utilisée pour catégoriser les travaux de rénovation énergétique utilise un format textuel `tags . valeur`. Cette approche présente plusieurs avantages :

- Les clés étrangères implémentées par les producteurs de données métiers sont lisibles et compréhensibles. Une clé étrangère `chauffage et eau chaude sanitaire . système solaire . système solaire combiné` traduit davantage son objet métier qu'une clé alphanumérique.

- La codification est immutable par essence : un système solaire combiné sera toujours un système solaire et relèvera toujours de travaux sur le chauffage et l'eau chaude sanitaire. De nouvelles catégories peuvent être ajoutées, d'autres dépréciées, mais une valeur associée à un système de tags à un instant t sera toujours cohérente.

- Le Self-Referencing (l'association d'une liaison d'une ligne d'une table vers une autre ligne de la même table) est géré nativement par la concaténation des tags.

- Le coût supplémentaire pour les producteurs de données lié à l'intégration d'une clé étrangère textuelle peut être résolue par la création d'une table opendata ad hoc (abstraction). 

- L'utilisation d'une ressource textuelle comme clé étrangère permet d'exploiter les modèles de langage afin d'enrichir les données métiers.

#### Ventilation des travaux de rénovation énergétique

Une ventilation des travaux de rénovation énergétique par tags est proposée dans le fichier data/base_travaux.csv.

## 🔎 Sources de données

- [La liste des travaux utilisée dans le cadre du service Simul'Aides de l'ADEME](https://data.ademe.fr/datasets/simul'aideuros-dispositifs-travaux)
- [La liste des fiches d'opérations standardisées d'économies d'énergie utilisée dans le cadre du dispositif des Certificats d'Economies d'Energie](https://github.com/CeeConnect/repertoire)
