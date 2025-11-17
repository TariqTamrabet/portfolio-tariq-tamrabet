---
layout: project
title: "Semantic Thesauru"
---

# Semantic Thesaurus – NLP & Word2Vec for Data Governance

## Contexte

Ce projet a été développé dans le cadre de ma mission au **Crédit Agricole Personal Finance & Mobility (CAPFM)**, au sein du **Data Management Office (DMO)**.  
Le DMO souhaitait renforcer la cohérence sémantique du **glossaire métier** utilisé dans **Collibra**, afin d’améliorer la recherche, la classification et la documentation des termes de données.  

L’objectif était de concevoir un **moteur de détection automatique des synonymes et relations sémantiques** basé sur des modèles de langage (NLP & Word2Vec), pour fiabiliser la gouvernance du vocabulaire métier.

---

## Objectif du projet

Développer un moteur sémantique permettant de :
- Identifier automatiquement les **synonymes et variantes lexicales** des termes métiers.  
- Enrichir le **glossaire Collibra** en détectant les relations entre concepts.  
- Créer un **data mart sémantique** dans Snowflake pour le stockage et la visualisation des résultats.  
- Offrir une **interface intuitive** pour la validation, la recherche et la visualisation des liens entre termes.  

---

## Architecture générale

L’architecture repose sur quatre modules complémentaires :  

| Module | Description |
|--------|--------------|
| **Traitement NLP (Python)** | Nettoyage, tokenisation et vectorisation des termes à partir des glossaires métiers. |
| **Modèle Word2Vec** | Entraînement sur corpus bancaire pour identifier les similarités entre termes. |
| **Stockage Snowflake** | Data mart sémantique centralisant les concepts, relations et scores de similarité. |
| **Interface Streamlit** | Application interactive pour visualiser, valider et exporter les synonymes vers Collibra. |

**Image 1 – Schéma d’architecture sémantique**

<p style="margin: 60px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/9bc57759-7f7a-4551-b006-26138df5ab04"
    alt="architecture sémantique"
    style="
      display:block;
      margin: 0 auto;
      width:100%;                       /* très large, comme pour Data Quality */
      max-width:1900px;
      border: 5px solid #000000;        /* cadre noir épais */
      border-radius: 12px;
      padding: 12px;
      background-color: #ffffff;
      box-shadow: 0 8px 28px rgba(0,0,0,0.25);
    ">
</p>

---

## Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | Python, SQL |
| **Bibliothèques NLP** | spaCy, Gensim (Word2Vec), NLTK |
| **Visualisation** | Streamlit, PyVis |
| **Base de données** | Snowflake |
| **Interopérabilité** | Collibra API (export des synonymes validés) |
| **Méthodologie** | Agile – itérations avec les Data Stewards |

---

## Modules fonctionnels

### 🔹 1. Préparation et structuration du glossaire métier
- Extraction et nettoyage des termes du glossaire Collibra.  
- Suppression des doublons, homogénéisation des formats (majuscule, pluriel, accents).  
- Enrichissement par ajout de métadonnées : domaine, business term, propriétaire, etc.  

**Image 2 – Échantillon du glossaire nettoyé**

<p style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/60fb76a7-bfb8-4ad2-8e74-f1a40b9afb47"
    alt="glossaire nettoyé"
    style="
      display:block;
      margin: 0 auto;
      width:100%;                       /* agrandi */
      max-width:1600px;                 /* large mais contrôlé */
      border: 4px solid #000000;
      border-radius: 10px;
      padding: 10px;
      background-color: #ffffff;
      box-shadow: 0 6px 22px rgba(0,0,0,0.25);
    ">
</p>

---

### 🔹 2. Entraînement du modèle NLP
- Constitution d’un **corpus métier** à partir de descriptions, rapports et termes Collibra.  
- Vectorisation des mots avec **Word2Vec** (modèle CBOW).  
- Calcul de la **similarité cosinus** pour mesurer la proximité sémantique entre termes.  
- Génération d’un graphe relationnel des concepts similaires.

**Image 3 – Graphe sémantique Word2Vec**

<p style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/51e59fc6-ca09-47c9-a0bd-d6895865c9fd"
    alt="graphe word2vec"
    style="
      display:inline-block;
      width:65%;                        /* plus petit, comme l’image 3 de l’autre projet */
      max-width:900px;
      border: 3px solid #000000;
      border-radius: 10px;
      padding: 8px;
      background-color: #ffffff;
      box-shadow: 0 5px 18px rgba(0,0,0,0.25);
    ">
</p>

---

### 🔹 3. Stockage et visualisation dans Snowflake
- Insertion des résultats du modèle (termes, scores, liens sémantiques) dans des tables dédiées.  
- Mise à jour automatique du **data mart sémantique** après chaque itération du modèle.  
- Intégration de filtres pour l’exploration par domaine, langue ou type de relation.

**Image 4 – Structure du data mart sémantique (Snowflake)**

<p style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/c4011c14-5e85-49ec-be5d-54c259e76e91"
    alt="data mart sémantique"
    style="
      display:inline-block;
      width:55%;                        /* intermédiaire */
      max-width:1000px;
      border: 3px solid #000000;
      border-radius: 10px;
      padding: 8px;
      background-color: #ffffff;
      box-shadow: 0 6px 20px rgba(0,0,0,0.25);
    ">
</p>

---

### 🔹 4. Interface Streamlit – Validation et export
- Application Streamlit permettant de :
  - Rechercher un terme et afficher ses synonymes suggérés.  
  - Visualiser le graphe des relations sémantiques (PyVis).  
  - Valider ou rejeter les suggestions.  
  - Exporter les synonymes validés au format “Collibra Ready”.  

---

## Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Termes analysés** | +350 |
| **Relations générées** | +500 |
| **Taux de précision du modèle** | 80 % |
| **Synonymes validés** | 420 |
| **Données stockées** | 6 tables Snowflake (concepts, relations, logs, etc.) |

---

## Livrables produits

| Type | Description |
|------|--------------|
| **Modèle NLP (Word2Vec)** | Détection automatique de synonymes à partir du corpus métier. |
| **Data Mart Snowflake** | Base sémantique centralisée pour le stockage et la requête des relations. |
| **Application Streamlit** | Interface de validation et d’export pour les Data Stewards. |
| **Exports Collibra Ready** | Fichiers normalisés pour mise à jour du glossaire Collibra. |
| **Documentation technique** | Guide d’utilisation, scripts Python et schémas Snowflake. |

---

## Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **Corpus restreint** | Modèle entraîné uniquement sur un vocabulaire bancaire interne. | Enrichir le corpus avec des textes sectoriels et open data. |
| **Ambiguïté lexicale** | Certains termes polysémiques génèrent de faux positifs. | Ajout d’un module de désambiguïsation contextuelle (spaCy). |
| **Validation manuelle** | Validation humaine nécessaire pour 20 % des suggestions. | Intégration d’un module semi-supervisé d’apprentissage continu. |

**Image 5 – Pipeline NLP simplifié**

<p style="margin: 50px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/8938ec29-03b0-41bb-b074-833c61ec5838"
    alt="pipeline nlp"
    style="
      display:inline-block;
      width:80%;
      max-width:900px;
      border: 3px solid #000000;
      border-radius: 10px;
      padding: 8px;
      background-color: #ffffff;
      box-shadow: 0 6px 20px rgba(0,0,0,0.25);
    ">
</p>

---

## Impacts et valeur ajoutée

- **Harmonisation du vocabulaire métier** à l’échelle du groupe.  
- **Amélioration de la recherche Collibra** grâce à la reconnaissance des synonymes.  
- **Gain de productivité** pour les Data Stewards lors de la mise à jour du glossaire.  
- **Réduction des redondances** et incohérences dans la documentation.  
- **Intégration facilitée** des concepts dans la gouvernance globale des données.  

<p style="margin: 40px 0; text-align: center;">
  <img 
    src="https://github.com/user-attachments/assets/ca6696c1-6fac-4313-96a4-45667aa9e2ad"
    alt="illustration"
    style="
      display:inline-block;
      width:500px;
      height:200px;
      border: 3px solid #000000;
      border-radius: 10px;
      padding: 6px;
      background-color: #ffffff;
      box-shadow: 0 4px 16px rgba(0,0,0,0.25);
    ">
</p>

---

## Enseignements

- Le **traitement sémantique** est un levier puissant pour la gouvernance des données.  
- La **collaboration entre data scientists et métiers** est clé pour la pertinence du modèle.  
- L’intégration du NLP dans la gouvernance ouvre la voie à une **intelligence documentaire continue**.  

---

## Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

### Prochain projet → [Data Quality Dashboard](../data-quality-dashboard/)

> *“Structurer le langage des données, c’est renforcer la compréhension des métiers.”*
