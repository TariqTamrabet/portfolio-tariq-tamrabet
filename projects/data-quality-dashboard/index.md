---
layout: project
title: "Data Quality Dashboard"
---

# Data Quality Dashboard – Suivi et Pilotage des Indicateurs de Qualité

## Contexte

Ce projet a été conçu dans le cadre de mon alternance au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO a pour rôle de superviser la qualité, la conformité et la fiabilité des données utilisées dans les processus métiers et réglementaires.  

Le besoin exprimé par les équipes métiers était de disposer d’un outil de pilotage visuel centralisant les indicateurs de qualité de données (complétude, unicité, cohérence, conformité) issus de différentes sources.

---

## Objectif du projet

Développer un tableau de bord Power BI connecté à Snowflake permettant de :
- Suivre en temps réel les KPI de qualité pour chaque domaine métier (client, crédit, risque, conformité, référentiel).  
- Identifier rapidement les anomalies et écarts par rapport aux seuils de contrôle.  
- Fournir aux Data Stewards et managers une vision consolidée et dynamique de la qualité des données.  
- Faciliter la prise de décision et la priorisation des plans de remédiation.

---

## Architecture fonctionnelle

Le système repose sur une chaîne automatisée d’alimentation, de calcul et de restitution des indicateurs.

<table style="margin: 40px auto; border-collapse: collapse; width: 90%; text-align: left; font-size: 16px; border: 2px solid #1f77b4; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <thead>
    <tr style="background-color: #e9f2fb; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Couche</th>
      <th style="padding: 12px;">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding: 10px; font-weight: bold;">Source Snowflake</td><td style="padding: 10px;">Tables alimentées par les contrôles de qualité issus des règles DQ automatisées.</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">ETL Python / SQL</td><td style="padding: 10px;">Nettoyage, transformation et agrégation des résultats par domaine et KPI.</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Data Mart Qualité</td><td style="padding: 10px;">Structure normalisée dans Snowflake pour exposition vers Power BI.</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Dashboard Power BI</td><td style="padding: 10px;">Visualisation interactive des scores, tendances et anomalies.</td></tr>
  </tbody>
</table>

### Image 1 – Schéma d’architecture du dashboard Data Quality
<p style="margin: 60px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/3ef9b9d5-fbe9-4517-9e67-d2f2e67ab14b" 
    alt="architecture"
    style="
      display:block;
      margin: 0 auto;                   /* centrage parfait */
      width:100%;                       /* taille maximale dans la zone de contenu */
      max-width:1700px;                 /* grande largeur sur écran large */
      border: 5px solid #000000;        /* cadre noir */
      border-radius: 12px;
      padding: 12px;
      background-color: #ffffff;
      box-shadow: 0 8px 28px rgba(0,0,0,0.25);
    ">
</p>





---

## Stack technique

<table style="margin: 40px auto; border-collapse: collapse; width: 85%; text-align: left; font-size: 16px; border: 2px solid #1f77b4; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.1);">
  <thead>
    <tr style="background-color: #e9f2fb; border-bottom: 2px solid #1f77b4;">
      <th style="padding: 12px;">Domaine</th>
      <th style="padding: 12px;">Outils / Technologies</th>
    </tr>
  </thead>
  <tbody>
    <tr><td style="padding: 10px; font-weight: bold;">Langages</td><td style="padding: 10px;">Python, SQL</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Cloud / Stockage</td><td style="padding: 10px;">Snowflake</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">ETL & Automatisation</td><td style="padding: 10px;">Python (pandas, openpyxl), procédures Snowflake</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Visualisation</td><td style="padding: 10px;">Power BI</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Interopérabilité</td><td style="padding: 10px;">Export CSV / Excel vers Collibra et reporting DMO</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Méthodologie</td><td style="padding: 10px;">Agile – sprints hebdomadaires avec Data Stewards</td></tr>
  </tbody>
</table>

---

## Modules fonctionnels

### 1. Calcul et consolidation des KPI
- Extraction des règles de qualité exécutées dans Snowflake.  
- Calcul des scores de complétude, unicité, cohérence et conformité.  
- Agrégation par domaine, entité et type de donnée.  

### Image 2 – Exemple de tableau d’indicateurs consolidés
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/cb3e8060-c44c-406c-a246-65901a587fa8"
    alt="indicateurs"
    style="
      display:inline-block;
      width:85%;
      max-width:1100px;
      border: 4px solid #000000;          /* cadre noir épais */
      border-radius: 10px;                /* coins légèrement arrondis */
      padding: 8px;                       /* espace interne autour de l'image */
      background-color: #ffffff;          /* fond blanc pour bien détacher du fond */
      box-shadow: 0 6px 22px rgba(0,0,0,0.25); /* ombre douce et contrastée */
    ">
</p>


---

### 2. Modélisation du Data Mart
- Création d’un modèle logique centré sur les entités “Règle”, “KPI”, “Domaine”, “Score”.  
- Construction de vues dynamiques pour les dashboards Power BI.  
- Historisation automatique des résultats par date et exécution.  

### Image 3 – Schéma du modèle de données
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/512742a4-d9a8-4885-a410-6c08af116b98"
    alt="model"
    style="
      display:inline-block;
      width:80%;                       /* taille légèrement réduite */
      max-width:1000px;                /* limite raisonnable pour garder la netteté */
      border: 3px solid #000000;       /* cadre noir élégant */
      border-radius: 10px;             /* coins arrondis légers */
      padding: 8px;                    /* espace interne équilibré */
      background-color: #ffffff;       /* fond blanc neutre */
      box-shadow: 0 5px 18px rgba(0,0,0,0.25); /* ombre douce pour relief */
    ">
</p>


---

### 3. Dashboard Power BI – Suivi global de la qualité
- Tableau de bord interactif affichant les scores par domaine, tendance temporelle et taux d’erreurs.  
- Navigation par filtres dynamiques (pays, entité, domaine, type de donnée).  
- Visualisation instantanée des règles en alerte ou non conformes.  
- Export PDF automatique pour diffusion en comité DMO.  

### Image 4 – Dashboard Power BI – Vue d’ensemble
<p align="center" style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/d869a103-aab9-4a12-a4e0-59ae3981da4e"
    alt="dashboard"
    style="
      display:inline-block;
      width:85%;
      max-width:1200px;
      border-radius: 10px;
      padding: 10px;
      background-color: #f8f9fa;
      box-shadow: 0 6px 20px rgba(0,0,0,0.2);
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
    <tr><td style="padding: 10px; font-weight: bold;">KPI suivis</td><td style="padding: 10px;">40+ indicateurs automatisés</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Domaines couverts</td><td style="padding: 10px;">5 (Clients, Crédit, Risque, Conformité, Référentiels)</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Fréquence de mise à jour</td><td style="padding: 10px;">Quotidienne</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Utilisateurs actifs</td><td style="padding: 10px;">30 Data Stewards et Managers</td></tr>
    <tr><td style="padding: 10px; font-weight: bold;">Réduction du temps de reporting</td><td style="padding: 10px;">-70 %</td></tr>
  </tbody>
</table>

---

## Impacts et valeur ajoutée

- Visibilité consolidée sur la qualité de données à l’échelle du groupe.  
- Réactivité accrue dans la détection des anomalies.  
- Meilleure collaboration entre métiers et data teams autour des KPI communs.  
- Fiabilisation du reporting réglementaire (BCBS 239, RGPD).  
- Réduction des tâches manuelles grâce à l’automatisation du calcul et du suivi.

---

## Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

### Prochain projet → [Data Governance Automation](../data-governance-automation/)

> *“Mesurer la qualité des données, c’est mesurer la confiance dans l’entreprise.”*
