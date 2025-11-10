# 🧩 Application de Data Governance & Data Quality Automation

## 🏢 Contexte

Ce projet a été développé dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO a pour mission de piloter la gouvernance et la qualité des données, en garantissant leur conformité, leur fiabilité et leur valorisation.  

👉 L’application a été conçue pour **automatiser la documentation, l’historisation et la visualisation** des règles de qualité des données dans un écosystème cloud.

---

## 🎯 Objectif du projet

Développer une solution **end-to-end** pour :
- Centraliser et normaliser les **règles de qualité**.  
- Assurer leur **historisation et traçabilité** dans Snowflake.  
- Générer automatiquement les **exports vers Collibra**.  
- Permettre un **suivi visuel temps réel** via Power BI.  

---

## 🧠 Architecture générale

L’application repose sur une architecture en 5 couches interconnectées :

| Couche | Description |
|--------|--------------|
| **Interface Streamlit** | Interface ergonomique pour la saisie et la visualisation des règles qualité. |
| **Back-end Python / SQL** | Traitement, transformation et historisation des données. |
| **Base Snowflake** | Stockage et historisation des règles, logs et résultats. |
| **Dashboard Power BI** | Visualisation des indicateurs et alertes. |
| **Interopérabilité Collibra** | Génération des fichiers d’export prêts à l’import. |

📸 **Image 1 – Schéma d’architecture globale <img width="592" height="653" alt="image" src="https://github.com/user-attachments/assets/08d8141a-07a5-448f-afb0-da575cb070a8" />
)**  
*(Suggestion : diagramme fonctionnel montrant Streamlit ↔ Python ↔ Snowflake ↔ Power BI / Collibra)*

---

## ⚙️ Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | Python, SQL |
| **Cloud / Stockage** | Snowflake |
| **ETL & Automatisation** | Python (pandas, openpyxl, streamlit) |
| **Visualisation** | Power BI |
| **Interopérabilité** | Collibra API (préparée, non encore déployée) |
| **Méthodologie** | Agile – Sprints hebdomadaires DMO |

---

## 🧩 Modules fonctionnels

### 🔹 1. Documentation des règles de qualité
- Import automatisé de modèles Excel.  
- Normalisation du format et validation automatique des colonnes.  
- Association métier-technique (Business Term ↔ Data Field).  
- Export de fichiers normalisés “Collibra Ready”.

📸 **Image 2 – Interface Streamlit : Module Documentation (à insérer ici)**  
*(Suggestion : capture du formulaire d’import ou de la liste des règles)*

---

### 🔹 2. Historisation et traçabilité
- Chaque exécution crée une nouvelle version horodatée.  
- Historisation complète dans Snowflake avec logs détaillés.  
- Comparaison temporelle des versions (ex : anomalies + tendances).

📸 **Image 3 – Interface Streamlit : Module Historisation (à insérer ici)**  
*(Suggestion : capture montrant la liste des versions ou logs d’historique)*

📸 **Image 4 – Schéma de tables Snowflake (à insérer ici)**  
*(Suggestion : tables DQ_RULES, DQ_HISTORY, DQ_LOGS, etc.)*

---

### 🔹 3. Export “Collibra Ready”
- Génération automatique des fichiers prêts à l’import dans Collibra.  
- Champs standardisés : `Rule_ID`, `Business_Term`, `Metric`, `Domain`, `Last_Update`.  
- Contrôles de cohérence avant export.

📸 **Image 5 – Exemple de fichier exporté pour Collibra (à insérer ici)**  
*(Suggestion : aperçu d’un fichier Excel généré automatiquement)*

---

### 🔹 4. Dashboard Power BI – Data Quality Monitoring
- Suivi des KPI de fiabilité et conformité : complétude, cohérence, unicité, conformité.  
- Visualisation dynamique des alertes et scores de qualité.  
- Rapports exportables en PDF pour les comités DMO.

📸 **Image 6 – Dashboard Power BI (à insérer ici)**  
*(Suggestion : capture des indicateurs clés et du graphique d’évolution)*

---

## 📈 Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Règles documentées** | +300 |
| **KPI suivis** | 10 |
| **Domaines couverts** | 5 (clients, crédit, risques, conformité, référentiels) |
| **Utilisateurs actifs** | 25 Data Stewards & Managers |
| **Gain de temps** | +60 % sur la documentation et les contrôles manuels |

📸 **Image 7 – Graphique Power BI : évolution du score qualité (à insérer ici)**

---

## 🗂️ Livrables produits

| Type | Description |
|------|--------------|
| **Application Web** | Interface Streamlit modulaire (documentation, historisation, export) |
| **Pipeline ETL** | Python / SQL automatisant les traitements vers Snowflake |
| **Tableaux de bord** | Power BI connectés en direct à Snowflake |
| **Exports Collibra** | Fichiers Excel/CSV standardisés |
| **Fichiers de logs** | Historisation automatique des exécutions et erreurs |

📸 **Image 8 – Exemple d’écran de logs ou exécution réussie (à insérer ici)**

---

## 🚧 Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **API Collibra non implémentée** | Les exports se font encore par fichier Excel. | Prévoir un connecteur REST Collibra (OAuth 2.0). |
| **Jeux de tests simulés** | Absence de données réelles au départ. | Génération automatique via scripts Python. |
| **Évolutions Snowflake** | Modifications fréquentes des schémas. | Refactoriser le modèle de données + vues dynamiques. |

📸 **Image 9 – Schéma de flux ETL ou pipeline Python (à insérer ici)**

---

## 🌍 Impacts et valeur ajoutée

- **Conformité accrue** (RGPD, BCBS 239) grâce à la traçabilité intégrée.  
- **Réduction de la charge mentale** des Data Stewards via l’automatisation.  
- **Collaboration renforcée** entre métiers, IT et Data Management.  
- **Culture Data** consolidée au sein du DMO (meilleure appropriation des outils).

📸 **Image 10 – Exemple de vue utilisateur ou workflow collaboratif (à insérer ici)**

---

## 📚 Enseignements

- L’importance d’une **architecture modulaire** pour faciliter les évolutions.  
- La **co-construction avec les métiers** est clé pour l’adoption.  
- Une bonne **gouvernance des métadonnées** améliore la performance globale des équipes data.  

---

## 👨‍💻 Auteur

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

📦 **Prochain projet → [Semantic Thesaurus](../semantic-thesaurus/)**
