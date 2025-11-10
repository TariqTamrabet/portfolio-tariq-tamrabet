# 🧩 Application de Data Governance & Data Quality Automation

## 🎯 Contexte

Ce projet a été réalisé dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO pilote la gouvernance des données de l’entreprise et a pour mission de fiabiliser, documenter et valoriser les actifs data.

Dans ce contexte, j’ai conçu et développé une **application complète de Data Quality Management** destinée à automatiser la documentation, l’historisation et la visualisation des règles de qualité des données.

---

## 🧠 Objectif du projet

Créer une solution **end-to-end** permettant :
- La **centralisation** des règles de qualité dans un format unifié.  
- L’**automatisation** du traitement et de l’historisation des résultats.  
- L’**export automatique** des fichiers vers **Collibra** (glossaire de gouvernance).  
- La **visualisation dynamique** des indicateurs dans **Power BI**.

---

## 🏗️ Architecture du système

L’application repose sur une architecture modulaire intégrant plusieurs couches :

| Couche | Description |
|--------|--------------|
| **Interface (Streamlit)** | Interface utilisateur simple et interactive, destinée aux Data Stewards et Data Managers. |
| **Back-end (Python / SQL)** | Scripts de traitement et de transformation des règles qualité. |
| **Stockage (Snowflake)** | Base de données cloud pour historisation, logs et data mart qualité. |
| **Reporting (Power BI)** | Dashboard connecté à Snowflake pour suivi temps réel. |
| **Interopérabilité (Collibra)** | Génération automatique des fichiers prêts à l’import dans le data catalog. |

📊 **Schéma fonctionnel simplifié :**
<img width="611" height="311" alt="image" src="https://github.com/user-attachments/assets/4b5b825e-7d56-4df1-8a13-c40178496900" />
