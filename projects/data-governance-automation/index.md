# Application de Data Governance & Data Quality Automation

## Contexte

Ce projet a été conçu dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO a pour mission de piloter la **gouvernance, la qualité et la valorisation des données**, tout en garantissant leur conformité réglementaire et leur fiabilité opérationnelle.  

L’application développée vise à **automatiser la documentation, l’historisation et la visualisation** des règles de qualité des données au sein d’un environnement cloud intégré.

---

## Objectif du projet

Développer une solution **end-to-end** permettant de :
- Centraliser et normaliser les **règles de qualité des données**.  
- Assurer leur **traçabilité et historisation** dans **Snowflake**.  
- Générer automatiquement les **exports vers Collibra**.  
- Offrir un **suivi visuel en temps réel** via des tableaux de bord **Power BI**.  

---

## Architecture générale

L’application repose sur une architecture **modulaire et interconnectée** composée de cinq couches principales :

| Couche | Description |
|--------|--------------|
| **Interface Streamlit** | Application web intuitive pour la saisie, la consultation et la validation des règles de qualité. |
| **Back-end Python / SQL** | Gestion des traitements, transformations et contrôles de cohérence des données. |
| **Snowflake Data Warehouse** | Stockage centralisé et historisation des règles, logs et résultats d’exécution. |
| **Power BI Dashboard** | Suivi dynamique des indicateurs de fiabilité, conformité et performance. |
| **Interopérabilité Collibra** | Génération automatisée des exports “Collibra Ready” pour intégration au data catalog. |

📸 **Image 1 – Schéma d’architecture globale**

<img width="592" height="653" alt="architecture" src="https://github.com/user-attachments/assets/08d8141a-07a5-448f-afb0-da575cb070a8" />

---

## Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | Python, SQL |
| **Cloud / Stockage** | Snowflake |
| **ETL & Automatisation** | Python (pandas, openpyxl, streamlit) |
| **Visualisation** | Power BI |
| **Interopérabilité** | Collibra API (préparée, en phase d’intégration) |
| **Méthodologie** | Agile – sprints hebdomadaires DMO |

---

## Modules fonctionnels

### 🔹 1. Documentation des règles de qualité
- Import automatique de modèles Excel et validation de la conformité des formats.  
- Normalisation et alignement des champs selon les standards DMO.  
- Association des éléments **métier ↔ technique** (Business Term ↔ Data Field).  
- Export automatisé des fichiers au format “Collibra Ready”.

📸 **Image 2 – Interface Streamlit : Module Documentation**

<img width="548" height="243" alt="interface" src="https://github.com/user-attachments/assets/a95a5490-aed5-4a17-892d-f7fd0a32f1f1" />

---

### 🔹 2. Historisation et traçabilité
- Création automatique de versions horodatées à chaque exécution.  
- Stockage dans Snowflake avec enregistrement des logs et anomalies.  
- Comparaison temporelle des indicateurs pour détecter les écarts et évolutions.

📸 **Image 3 – Schéma de tables Snowflake**

<img width="684" height="272" alt="snowflake" src="https://github.com/user-attachments/assets/a3b140ed-e0c0-4529-b5de-35cf3081cc3b" />

---

### 🔹 3. Export “Collibra Ready”
- Génération automatique de fichiers normalisés prêts à l’import dans Collibra.  
- Champs standards : `Rule_ID`, `Business_Term`, `Metric`, `Domain`, `Last_Update`.  
- Contrôle des formats, vérification des doublons et cohérence métier.  

---

### 🔹 4. Dashboard Power BI – Data Quality Monitoring
- Visualisation interactive des KPI : complétude, cohérence, unicité, conformité.  
- Segmentation par domaine métier et par niveau de criticité.  
- Génération automatique de rapports PDF pour les comités Data Quality.

📸 **Image 4 – Dashboard Power BI**

<img width="499" height="339" alt="dashboard" src="https://github.com/user-attachments/assets/cf5effc9-0f98-4d9b-b865-ae635f1a9c8c" />

---

## Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Règles documentées** | +300 |
| **KPI suivis** | 10 |
| **Domaines couverts** | 5 (Clients, Crédit, Risques, Conformité, Référentiels) |
| **Utilisateurs actifs** | 25 Data Stewards & Managers |
| **Gain de temps** | +60 % sur la documentation et les contrôles manuels |

**Image 5 – Évolution du score de qualité**

<img width="635" height="376" alt="graphique" src="https://github.com/user-attachments/assets/95a45e99-b611-4e90-a434-42014d84e9bc" />

---

## Livrables produits

| Type | Description |
|------|--------------|
| **Application Web** | Interface Streamlit modulaire (documentation, historisation, export). |
| **Pipeline ETL** | Scripts Python / SQL automatisant les traitements et contrôles vers Snowflake. |
| **Dashboards Power BI** | Tableaux de bord connectés à Snowflake pour suivi temps réel. |
| **Exports Collibra** | Fichiers CSV / Excel prêts à l’import. |
| **Logs d’exécution** | Historisation et traçabilité des traitements automatisés. |

📸 **Image 6 – Exemple de logs et exécution réussie**

<img width="600" height="354" alt="logs" src="https://github.com/user-attachments/assets/053763f6-1419-4b52-8634-3bb02fe5b4d9" />

---

## Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **API Collibra non implémentée** | Les exports sont encore manuels (fichier Excel). | Déploiement d’un connecteur REST Collibra (OAuth 2.0). |
| **Jeux de tests simulés** | Absence de données réelles initialement. | Génération automatique via scripts Python. |
| **Évolution du schéma Snowflake** | Modifications fréquentes selon les domaines. | Création de vues dynamiques et modèle unifié. |

**Image 7 – Schéma de flux ETL**

<img width="1200" height="300" alt="pipeline" src="https://github.com/user-attachments/assets/e8970a5a-0645-45de-8969-73a3c4c186f2" />

---

## Impacts et valeur ajoutée

- **Conformité renforcée** : traçabilité complète des règles (RGPD, BCBS 239).  
- **Gain de productivité** : automatisation des tâches manuelles à faible valeur ajoutée.  
- **Amélioration de la qualité des données** : réduction significative des écarts et anomalies.  
- **Collaboration accrue** : meilleure communication entre métiers, IT et Data Office.  
- **Acculturation Data** : appropriation de la gouvernance par les utilisateurs finaux.  

<img width="320" height="200" alt="collaboration" src="https://github.com/user-attachments/assets/e2793f38-0e65-4513-a544-217b2cc94e96" />

---

##  Enseignements

- L’importance d’une **architecture modulaire et évolutive** pour la scalabilité.  
- La **co-construction métier / IT** favorise l’adoption et la pertinence fonctionnelle.  
- Une **gouvernance des métadonnées robuste** est un levier de performance durable.  

---

## Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

### 🔗 Prochain projet → [Semantic Thesaurus](../semantic-thesaurus/)

---

> *“Construire des données fiables, c’est construire la confiance dans les décisions.”*
