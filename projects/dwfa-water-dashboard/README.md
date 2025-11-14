# DWFA – Tableau de Bord Mondial sur l’Accès à l’Eau Potable

## Contexte

Ce projet a été réalisé dans le cadre du programme **GIS5 2024/2025**, pour l’ONG internationale **DWFA – Drinking Water For All**, qui œuvre pour garantir un **accès universel à l’eau potable**.  
L’objectif était de concevoir un **tableau de bord interactif sous Tableau Software** permettant de visualiser les **indicateurs clés liés à l’accès à l’eau potable** à différentes échelles : mondiale, continentale et nationale.  

L’outil permet à DWFA d’identifier les zones prioritaires, de **cibler les interventions stratégiques** et de **justifier les décisions auprès des bailleurs de fonds**.

## Objectif du projet

Concevoir une solution visuelle permettant à DWFA de :
- Analyser et comparer les **indicateurs d’accès à l’eau potable** dans le monde.  
- Identifier les zones où les **risques sanitaires et les besoins en infrastructures** sont les plus élevés.  
- Faciliter la **planification des actions par domaine d’expertise** (création, modernisation, consulting).  
- Proposer un **outil interactif** et ergonomique, utilisable par les décideurs et les analystes.

## Architecture du tableau de bord

| Niveau d’analyse | Description |
|------------------|-------------|
| **Vue Globale** | Analyse mondiale de l’accès à l’eau, de la mortalité liée à l’eau insalubre, de la densité de population et de la stabilité politique. |
| **Vue Continentale** | Comparaison des indicateurs entre continents avec suivi temporel. |
| **Vue Nationale** | Analyse détaillée par pays, combinant accès à l’eau, croissance démographique et stabilité politique. |

**Image 1 – Schéma de structure du dashboard**

<img width="700" alt="structure" src="https://github.com/user-attachments/assets/f6a34ffb-3a6d-4f4e-9c3d-6b1b8a2e2f21" />

## Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Outil principal** | Tableau Software |
| **Données** | Banque Mondiale, UNICEF, OMS |
| **Langages** | Champs calculés (Tableau), SQL (préparation) |
| **Visualisation** | Cartes choroplèthes, nuages de points, barres comparatives |
| **Export** | Tableaux interactifs, rapports visuels |
| **Méthodologie** | Approche analytique – itérative par vues |

## Sélection des indicateurs clés

| Indicateur | Description | Utilité |
|-------------|--------------|----------|
| **Taux d’accès à l’eau potable** | Pourcentage de la population disposant d’un accès à l’eau de base ou sécurisée. | Identifier les zones à faible couverture. |
| **Taux de mortalité dû à l’eau insalubre** | Mesure de l’impact sanitaire du manque d’eau potable. | Prioriser les zones à risque. |
| **Densité de population** | Nombre d’habitants par km². | Identifier les zones à forte demande en infrastructures. |
| **Stabilité politique** | Indice de gouvernance mondiale. | Évaluer la faisabilité des projets. |

**Image 2 – Exemple de carte mondiale sur l’accès à l’eau potable**

<img width="1271" height="817" alt="image" src="https://github.com/user-attachments/assets/f545464b-c2c3-41c3-bbfc-9afd65d0e7bc" />


## Domaines d’expertise DWFA et visualisations associées

### 1. Création de services d’accès à l’eau
- Indicateurs : taux d’accès à l’eau potable et taux de population urbaine.  
- Objectif : cibler les zones de forte croissance démographique à faible couverture.  
- Visualisation : **nuage de points** liant urbanisation et accès à l’eau.

**Image 3 – Relation entre taux d’accès et population urbaine**

<img width="650" alt="scatter1" src="https://github.com/user-attachments/assets/b18f2b32-0f53-4bb5-a145-8d0edfb743b1" />

### 2. Modernisation des services existants
- Indicateurs : taux de services basiques vs taux de services sécurisés.  
- Objectif : identifier les pays ayant besoin d’améliorer la qualité des infrastructures.  
- Visualisation : **nuage de points** comparant les deux niveaux de service.

**Image 4 – Comparaison entre services basiques et sécurisés**

<img width="580" height="582" alt="image" src="https://github.com/user-attachments/assets/575aa92c-6e2d-4254-a2af-d2f3b6b88503" />



### 3. Consulting sur les politiques d’accès à l’eau
- Indicateurs : efficacité des politiques (accès vs mortalité) et stabilité politique.  
- Objectif : évaluer la faisabilité des projets de conseil gouvernemental.  
- Visualisation : **diagramme de corrélation** entre gouvernance et impact sanitaire.

**Image 5 – Évaluation de la stabilité et de l’efficacité politique**

<img width="1104" height="395" alt="image" src="https://github.com/user-attachments/assets/835e8c3e-3424-47a0-93f2-3c353e4e595a" />


## Résultats obtenus

| Critère | Résultat |
|----------|-----------|
| **Couverture mondiale** | 190 pays analysés |
| **Indicateurs traités** | 4 indicateurs principaux + 2 calculés |
| **Vues interactives** | 3 (mondiale, continentale, nationale) |
| **Filtres disponibles** | Année, continent, pays, granularité |
| **Tendances observées** | Amélioration globale de l’accès, mais fortes disparités régionales |

**Lien vers mon dashboard Tableau :** https://public.tableau.com/app/profile/tariq.tamrabet/viz/Projet_DataViz_TariqTAMRABET/Histoire1?publish=yes



## Impacts et valeur ajoutée

- Vision consolidée et dynamique de l’accès à l’eau potable.  
- Identification rapide des priorités géographiques et politiques.  
- Aide à la planification des programmes DWFA (infrastructures, modernisation, conseil).  
- Outil de communication efficace auprès des bailleurs et institutions partenaires.  
- Sensibilisation accrue à l’inégalité d’accès à l’eau potable.

## Enseignements

- L’importance des **données géospatiales et temporelles** pour le pilotage des politiques publiques.  
- La **corrélation entre stabilité politique et efficacité des infrastructures** est déterminante.  
- L’usage d’un **outil de visualisation interactif** renforce la prise de décision stratégique.

## Contact

**Tariq TAMRABET**  
*Data Analyst – Projet ONG Drinking Water For All (DWFA)*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

> *“L’eau potable n’est pas un privilège, c’est un droit fondamental.”*

