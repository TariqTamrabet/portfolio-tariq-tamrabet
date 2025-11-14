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

<table style="margin: 40px auto; border-collapse: collapse; width: 90%; text-align: left; font-size: 16px;">
  <thead>
    <tr style="background-color: #f8f9fa; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Couche</th>
      <th style="padding: 12px;">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Interface Streamlit</td>
      <td style="padding: 10px;">Application web intuitive pour la saisie, la consultation et la validation des règles de qualité.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Back-end Python / SQL</td>
      <td style="padding: 10px;">Gestion des traitements, transformations et contrôles de cohérence des données.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Snowflake Data Warehouse</td>
      <td style="padding: 10px;">Stockage centralisé et historisation des règles, logs et résultats d’exécution.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Power BI Dashboard</td>
      <td style="padding: 10px;">Suivi dynamique des indicateurs de fiabilité, conformité et performance.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Interopérabilité Collibra</td>
      <td style="padding: 10px;">Génération automatisée des exports “Collibra Ready” pour intégration au data catalog.</td>
    </tr>
  </tbody>
</table>


### Image 1 – Schéma flux globale
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/08d8141a-07a5-448f-afb0-da575cb070a8" 
    alt="architecture" 
    style="
      display:inline-block;
      width:95%;                /* agrandissement significatif et équilibré */
      max-width:1200px;         /* limite de largeur pour éviter la déformation */
      border: 3px solid #000000; /* encadrement bleu data */
      border-radius: 12px;
      padding: 12px;
      background-color: #f8f9fa;
      box-shadow: 0 6px 22px rgba(0,0,0,0.25);
    ">
</p>


---

## Stack technique

<table style="margin: 40px auto; border-collapse: collapse; width: 90%; text-align: left; font-size: 16px;">
  <thead>
    <tr style="background-color: #f8f9fa; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 10px;">Domaine</th>
      <th style="padding: 10px;">Outils / Technologies</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding: 10px; font-weight: bold;">Langages</td><td style="padding: 10px;">Python, SQL</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Cloud / Stockage</td><td style="padding: 10px;">Snowflake</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">ETL & Automatisation</td><td style="padding: 10px;">Python (pandas, openpyxl, streamlit)</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Visualisation</td><td style="padding: 10px;">Power BI</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Interopérabilité</td><td style="padding: 10px;">Collibra API (préparée, en phase d’intégration)</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Méthodologie</td><td style="padding: 10px;">Agile – sprints hebdomadaires DMO</td></tr>
  </tbody>
</table>


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
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/a3b140ed-e0c0-4529-b5de-35cf3081cc3b" 
    alt="snowflake" 
    style="
      display:inline-block;
      width:90%;                 /* agrandissement fluide */
      max-width:1200px;          /* limite raisonnable pour éviter le débordement */
      border: 3px solid #1f77b4; /* bleu data professionnel */
      border-radius: 12px;       /* coins arrondis doux */
      padding: 12px;             /* espace interne */
      background-color: #f8f9fa; /* fond clair élégant */
      box-shadow: 0 6px 22px rgba(0,0,0,0.25); /* ombre douce */
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
      width:70%;                        /* taille ajustée à 85 % */
      border-radius: 12px;               /* coins arrondis */
      padding: 8px;                      /* marge interne légère */
      background-color: #f8f9fa;         /* fond clair */
      box-shadow: 0 4px 16px rgba(0,0,0,0.15); /* ombre douce */
    ">
</p>



---

## Résultats obtenus

<table style="margin: 40px auto; border-collapse: collapse; width: 80%; text-align: left; font-size: 16px; border: 2px solid #1f77b4; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <thead>
    <tr style="background-color: #e9f2fb; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Indicateur</th>
      <th style="padding: 12px;">Résultat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Règles documentées</td>
      <td style="padding: 10px;">+ 300</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">KPI suivis</td>
      <td style="padding: 10px;">10</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Domaines couverts</td>
      <td style="padding: 10px;">5 (Clients, Crédit, Risques, Conformité, Référentiels)</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Utilisateurs actifs</td>
      <td style="padding: 10px;">25 Data Stewards & Managers</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Gain de temps</td>
      <td style="padding: 10px;">+ 60 % sur la documentation et les contrôles manuels</td>
    </tr>
  </tbody>
</table>


---

## Livrables produits

<table style="margin: 40px auto; border-collapse: collapse; width: 85%; text-align: left; font-size: 16px; border: 2px solid #1f77b4; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <thead>
    <tr style="background-color: #e9f2fb; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Type</th>
      <th style="padding: 12px;">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Application Web</td>
      <td style="padding: 10px;">Interface Streamlit modulaire (documentation, historisation, export).</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Pipeline ETL</td>
      <td style="padding: 10px;">Scripts Python / SQL automatisant les traitements et contrôles vers Snowflake.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Dashboards Power BI</td>
      <td style="padding: 10px;">Tableaux connectés à Snowflake pour le suivi temps réel.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Exports Collibra</td>
      <td style="padding: 10px;">Fichiers CSV / Excel prêts à l’import.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Logs d’exécution</td>
      <td style="padding: 10px;">Historisation et traçabilité automatisées.</td>
    </tr>
  </tbody>
</table>


---

## Contraintes et pistes d’amélioration

<table style="margin: 40px auto; border-collapse: collapse; width: 90%; text-align: left; font-size: 16px; border: 2px solid #1f77b4; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <thead>
    <tr style="background-color: #e9f2fb; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Limite</th>
      <th style="padding: 12px;">Description</th>
      <th style="padding: 12px;">Solution envisagée</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 10px; font-weight: bold;">API Collibra non implémentée</td>
      <td style="padding: 10px;">Exports encore manuels</td>
      <td style="padding: 10px;">Déploiement d’un connecteur REST (OAuth 2.0).</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Jeux de tests simulés</td>
      <td style="padding: 10px;">Données réelles absentes au démarrage</td>
      <td style="padding: 10px;">Génération automatique via scripts Python.</td>
    </tr>
    <tr>
      <td style="padding: 10px; font-weight: bold;">Évolution du schéma Snowflake</td>
      <td style="padding: 10px;">Modifications fréquentes selon les domaines</td>
      <td style="padding: 10px;">Création de vues dynamiques et modèle unifié.</td>
    </tr>
  </tbody>
</table>


### Image 4 – Schéma flux ETL
<p align="center" style="margin: 60px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/e8970a5a-0645-45de-8969-73a3c4c186f2" 
    alt="pipeline" 
    style="
      display:inline-block;
      width:92%;                 /* image bien visible sans dépasser */
      max-width:1300px;          /* limite pour les grands écrans */
      border: 3px solid #1f77b4; /* bleu data professionnel */
      border-radius: 12px;       /* coins arrondis */
      padding: 10px;             /* marge interne douce */
      background-color: #f8f9fa; /* fond clair et élégant */
      box-shadow: 0 8px 25px rgba(0,0,0,0.25); /* ombre plus profonde */
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
