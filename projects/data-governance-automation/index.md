---
layout: project
title: "Application de Data Governance & Data Quality Automation"
---

# Application de Data Governance & Data Quality Automation

## Contexte

Ce projet a été conçu dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO a pour mission de piloter la **gouvernance, la qualité et la valorisation des données**, tout en garantissant leur conformité réglementaire et leur fiabilité opérationnelle.  

L’application développée vise à **automatiser la documentation, l’historisation et la visualisation** des règles de qualité des données au sein d’un environnement cloud intégré.

---

## Objectif du projet

Développer une solution **end-to-end** permettant de :
- Centraliser et normaliser les **règles de qualité des données** ;  
- Assurer leur **traçabilité et historisation** dans **Snowflake** ;  
- Générer automatiquement les **exports vers Collibra** ;  
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

### Image 1 – Schéma d’architecture globale
<p align="center" style="margin: 40px 0;">
  <img 
    src="https://github.com/user-attachments/assets/08d8141a-07a5-448f-afb0-da575cb070a8" 
    alt="architecture" 
    style="
      display:block;
      max-width:95%;
      border: 2.5px solid #ccc;
      border-radius: 12px;
      padding: 8px;
      background-color: #fafafa;
      box-shadow: 0 4px 18px rgba(0,0,0,0.15);
    ">
</p>


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

### 1. Documentation des règles de qualité
- Import automatique de modèles Excel et validation des formats ;  
- Normalisation et alignement selon les standards DMO ;  
- Association des éléments **métier ↔ technique** ;  
- Export des fichiers au format *Collibra Ready*.  

### 2. Historisation et traçabilité
- Création automatique de versions horodatées à chaque exécution ;  
- Historisation complète dans Snowflake avec enregistrement des logs ;  
- Comparaison temporelle pour détecter les écarts et évolutions.  

### Image 2 – Schéma de tables Snowflake
<p align="center" style="margin: 40px 0;">
  <img 
    src="https://github.com/user-attachments/assets/a3b140ed-e0c0-4529-b5de-35cf3081cc3b" 
    alt="snowflake" 
    style="
      display:block;
      max-width:95%;
      border: 2.5px solid #000000; /* bleu data */
      border-radius: 12px;
      padding: 8px;
      background-color: #f8f9fa;
      box-shadow: 0 4px 18px rgba(0,0,0,0.15);
    ">
</p>


---

### 3. Export “Collibra Ready”
- Génération automatique de fichiers prêts à l’import ;  
- Champs : `Rule_ID`, `Business_Term`, `Metric`, `Domain`, `Last_Update` ;  
- Contrôles de cohérence et vérification des doublons.  

---

### 4. Dashboard Power BI – Data Quality Monitoring
- Visualisation interactive des KPI : complétude, cohérence, unicité, conformité ;  
- Segmentation par domaine métier et niveau de criticité ;  
- Rapports PDF générés pour les comités Data Quality.  

### Image 3 – Dashboard Power BI
<p align="center" style="margin: 40px 0;">
  <img 
    src="https://github.com/user-attachments/assets/cf5effc9-0f98-4d9b-b865-ae635f1a9c8c" 
    alt="dashboard" 
    style="
      display:block;
      width:80%;                        /* taille ajustée à 85 % */
      border: 2.5px solid #000000;       /* bordure bleue data */
      border-radius: 12px;               /* coins arrondis */
      padding: 8px;                      /* marge interne légère */
      background-color: #f8f9fa;         /* fond clair */
      box-shadow: 0 4px 16px rgba(0,0,0,0.15); /* ombre douce */
    ">
</p>



---

## Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Règles documentées** | + 300 |
| **KPI suivis** | 10 |
| **Domaines couverts** | 5 (Clients, Crédit, Risques, Conformité, Référentiels) |
| **Utilisateurs actifs** | 25 Data Stewards & Managers |
| **Gain de temps** | + 60 % sur la documentation et les contrôles manuels |

---

## Livrables produits

| Type | Description |
|------|--------------|
| **Application Web** | Interface Streamlit modulaire (documentation, historisation, export). |
| **Pipeline ETL** | Scripts Python / SQL automatisant les traitements et contrôles vers Snowflake. |
| **Dashboards Power BI** | Tableaux connectés à Snowflake pour le suivi temps réel. |
| **Exports Collibra** | Fichiers CSV / Excel prêts à l’import. |
| **Logs d’exécution** | Historisation et traçabilité automatisées. |

---

## Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **API Collibra non implémentée** | Exports encore manuels ; | Déploiement d’un connecteur REST (OAuth 2.0). |
| **Jeux de tests simulés** | Données réelles absentes au démarrage ; | Génération automatique via scripts Python. |
| **Évolution du schéma Snowflake** | Modifications fréquentes selon les domaines ; | Création de vues dynamiques et modèle unifié. |

### Image 4 – Schéma de flux
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/e8970a5a-0645-45de-8969-73a3c4c186f2" 
    alt="pipeline" 
    style="
      display:inline-block;
      width:95%;                        /* taille large mais proportionnée */
      border: 2.5px solid #000000;       /* bordure bleue data */
      border-radius: 12px;               /* coins arrondis */
      padding: 8px;                      /* marge interne légère */
      background-color: #f8f9fa;        /* fond clair */
      box-shadow: 0 6px 20px rgba(0,0,0,0.2); /* ombre douce */
    ">
</p>



---

## Impacts et valeur ajoutée

- **Conformité renforcée** : traçabilité complète des règles (RGPD, BCBS 239).  
- **Gain de productivité** : automatisation des tâches manuelles.  
- **Amélioration de la qualité des données** : réduction significative des anomalies.  
- **Collaboration accrue** : meilleure communication entre métiers et IT.  
- **Acculturation Data** : appropriation des outils par les utilisateurs finaux.  

---

## Enseignements

- L’importance d’une **architecture modulaire et évolutive** pour la scalabilité.  
- La **co-construction métier / IT** favorise l’adoption.  
- Une **gouvernance robuste des métadonnées** renforce la performance globale.  

---

## Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

### Prochain projet → [Semantic Thesaurus](../semantic-thesaurus/)

> *« Construire des données fiables, c’est construire la confiance dans les décisions. »*
