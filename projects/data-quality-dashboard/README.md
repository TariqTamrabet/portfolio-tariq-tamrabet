


# Data Quality Dashboard – Suivi et Pilotage des Indicateurs de Qualité

## Contexte

Ce projet a été conçu dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO a pour rôle de superviser la qualité, la conformité et la fiabilité des données utilisées dans les processus métiers et réglementaires.  

Le besoin exprimé par les équipes métiers était de disposer d’un outil de pilotage visuel centralisant les indicateurs de qualité de données (complétude, unicité, cohérence, conformité) issus de différentes sources.

## Objectif du projet

Développer un tableau de bord Power BI connecté à Snowflake permettant de :
- Suivre en temps réel les KPI de qualité pour chaque domaine métier (client, crédit, risque, conformité, référentiel).  
- Identifier rapidement les anomalies et écarts par rapport aux seuils de contrôle.  
- Fournir aux Data Stewards et managers une vision consolidée et dynamique de la qualité des données.  
- Faciliter la prise de décision et la priorisation des plans de remédiation.

## Architecture fonctionnelle

Le système repose sur une chaîne automatisée d’alimentation, de calcul et de restitution des indicateurs.

| Couche | Description |
|--------|--------------|
| **Source Snowflake** | Tables alimentées par les contrôles de qualité issus des règles DQ automatisées. |
| **ETL Python / SQL** | Nettoyage, transformation et agrégation des résultats par domaine et KPI. |
| **Data Mart Qualité** | Structure normalisée dans Snowflake pour exposition vers Power BI. |
| **Dashboard Power BI** | Visualisation interactive des scores, tendances et anomalies. |

**Image 1 – Schéma d’architecture du dashboard Data Quality**

<img width="4762" height="452" alt="Untitled diagram-2025-11-13-143515" src="https://github.com/user-attachments/assets/3ef9b9d5-fbe9-4517-9e67-d2f2e67ab14b" />


## Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | Python, SQL |
| **Cloud / Stockage** | Snowflake |
| **ETL & Automatisation** | Python (pandas, openpyxl), procédures Snowflake |
| **Visualisation** | Power BI |
| **Interopérabilité** | Export CSV / Excel vers Collibra et reporting DMO |
| **Méthodologie** | Agile – sprints hebdomadaires avec Data Stewards |

## Modules fonctionnels

### 1. Calcul et consolidation des KPI
- Extraction des règles de qualité exécutées dans Snowflake.  
- Calcul des scores de complétude, unicité, cohérence et conformité.  
- Agrégation par domaine, entité et type de donnée.  

**Image 2 – Exemple de tableau d’indicateurs consolidés**
<img width="1769" height="121" alt="image" src="https://github.com/user-attachments/assets/cb3e8060-c44c-406c-a246-65901a587fa8" />





### 2. Modélisation du Data Mart
- Création d’un modèle logique de données centré sur les entités “Règle”, “KPI”, “Domaine”, “Score”.  
- Construction de vues dynamiques pour les dashboards Power BI.  
- Historisation automatique des résultats par date et par exécution.

**Image 3 – Schéma du modèle de données**

<img width="292" height="253" alt="image" src="https://github.com/user-attachments/assets/512742a4-d9a8-4885-a410-6c08af116b98" />


### 3. Dashboard Power BI – Suivi global de la qualité
- Tableau de bord interactif affichant les scores par domaine, tendance temporelle et taux d’erreurs.  
- Navigation par filtres dynamiques (pays, entité, domaine, type de donnée).  
- Visualisation instantanée des règles en alerte ou non conformes.  
- Possibilité d’exporter les rapports PDF pour diffusion en comité Data Quality.  

**Image 4 – Dashboard Power BI – Vue d’ensemble**

<img width="693" height="497" alt="image" src="https://github.com/user-attachments/assets/d869a103-aab9-4a12-a4e0-59ae3981da4e" />

## Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **KPI suivis** | 40+ indicateurs automatisés |
| **Domaines couverts** | 5 (Clients, Crédit, Risque, Conformité, Référentiels) |
| **Fréquence de mise à jour** | Quotidienne |
| **Utilisateurs actifs** | 30 Data Stewards et Managers |
| **Réduction du temps de reporting** | -70 % |

**Image 5 – Évolution des scores de qualité**

<img width="461" height="327" alt="image" src="https://github.com/user-attachments/assets/806809d7-062b-4a8e-af73-0806f1f1ba0f" />


## Livrables produits

| Type | Description |
|------|--------------|
| **Dashboard Power BI** | Interface visuelle de pilotage des indicateurs DQ. |
| **Data Mart Snowflake** | Structure relationnelle d’exposition des KPI. |
| **Scripts Python / SQL** | Calcul et alimentation automatisée des indicateurs. |
| **Rapports PDF** | Export automatique pour les comités DMO. |
| **Documentation technique** | Dictionnaire de données et guide utilisateur. |


## Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **Volume croissant de données** | Temps de traitement plus long lors des extractions massives. | Optimisation des requêtes Snowflake et partitionnement. |
| **Manque d’indicateurs métier** | KPI techniques prédominants. | Co-construction de KPI métier avec les équipes locales. |
| **Visualisation statique** | Peu de scénarios prédictifs. | Ajout futur de modèles de scoring basés sur l’historique. |

**Image 6 – Schéma d’évolution du processus DQ**

<img width="1100" alt="pipeline" src="https://github.com/user-attachments/assets/faa9d94c-0875-4d17-b6dc-01a4b4cda6e2" />

## Impacts et valeur ajoutée

- Visibilité consolidée sur la qualité de données à l’échelle du groupe.  
- Réactivité accrue dans la détection des anomalies.  
- Meilleure collaboration entre métiers et data teams autour des KPI communs.  
- Fiabilisation du reporting réglementaire (BCBS 239, RGPD).  
- Réduction des tâches manuelles grâce à l’automatisation du calcul et du suivi.

**Image 7 – Tableau de bord consolidé (vue par domaine)**

<img width="700" alt="impact" src="https://github.com/user-attachments/assets/b3ad5b19-7a9a-4d55-9db8-5e2e2eb88419" />

## Enseignements

- La visualisation de la donnée est un levier clé pour la gouvernance et la responsabilisation.  
- L’industrialisation des contrôles qualité permet de gagner en fiabilité et en cohérence.  
- La co-construction des indicateurs avec les métiers favorise l’adoption et la pérennité de la démarche Data Quality.  

## Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

### Prochain projet → [Data Governance Automation](../data-governance-automation/)

> *“Mesurer la qualité des données, c’est mesurer la confiance dans l’entreprise.”*

