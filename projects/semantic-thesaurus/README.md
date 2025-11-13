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

📸 **Image 1 – Schéma d’architecture sémantique**

<img width="355" height="642" alt="Untitled diagram-2025-11-13-134101" src="https://github.com/user-attachments/assets/894c3242-0f8a-4151-96e1-0e139299d603" />





---

## ⚙️ Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | Python, SQL |
| **Bibliothèques NLP** | spaCy, Gensim (Word2Vec), NLTK |
| **Visualisation** | Streamlit, PyVis |
| **Base de données** | Snowflake |
| **Interopérabilité** | Collibra API (export des synonymes validés) |
| **Méthodologie** | Agile – itérations avec les Data Stewards |

---

## 🔍 Modules fonctionnels

### 🔹 1. Préparation et structuration du glossaire métier
- Extraction et nettoyage des termes du glossaire Collibra.  
- Suppression des doublons, homogénéisation des formats (majuscule, pluriel, accents).  
- Enrichissement par ajout de métadonnées : domaine, business term, propriétaire, etc.  

📸 **Image 2 – Échantillon du glossaire nettoyé**

<img width="600" alt="glossaire" src="https://github.com/user-attachments/assets/2c6378d3-9385-47a5-b8d8-74d1b8b06a89" />

---

### 🔹 2. Entraînement du modèle NLP
- Constitution d’un **corpus métier** à partir de descriptions, rapports et termes Collibra.  
- Vectorisation des mots avec **Word2Vec** (modèle CBOW).  
- Calcul de la **similarité cosinus** pour mesurer la proximité sémantique entre termes.  
- Génération d’un graphe relationnel des concepts similaires.

📸 **Image 3 – Graphe sémantique Word2Vec**

<img width="680" alt="word2vec" src="https://github.com/user-attachments/assets/3a24747e-9e2f-40e8-8c7f-3eb6cc428672" />

---

### 🔹 3. Stockage et visualisation dans Snowflake
- Insertion des résultats du modèle (termes, scores, liens sémantiques) dans des tables dédiées.  
- Mise à jour automatique du **data mart sémantique** après chaque itération du modèle.  
- Intégration de filtres pour l’exploration par domaine, langue ou type de relation.

📸 **Image 4 – Structure du data mart sémantique (Snowflake)**

<img width="700" alt="datamart" src="https://github.com/user-attachments/assets/4e5136e8-784a-47f0-a632-39a24863a877" />

---

### 🔹 4. Interface Streamlit – Validation et export
- Application Streamlit permettant de :
  - Rechercher un terme et afficher ses synonymes suggérés.  
  - Visualiser le graphe des relations sémantiques (PyVis).  
  - Valider ou rejeter les suggestions.  
  - Exporter les synonymes validés au format “Collibra Ready”.  

📸 **Image 5 – Interface Streamlit : Validation sémantique**

<img width="640" alt="interface" src="https://github.com/user-attachments/assets/65dfb3a5-f4ef-4ee0-968a-cacdb8f8b4a3" />

---

## 📈 Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Termes analysés** | +350 |
| **Relations générées** | +500 |
| **Taux de précision du modèle** | 80 % |
| **Synonymes validés** | 420 |
| **Données stockées** | 6 tables Snowflake (concepts, relations, logs, etc.) |

📊 **Image 6 – Graphe global des relations sémantiques**

<img width="700" alt="graph" src="https://github.com/user-attachments/assets/fcb01069-8a46-4417-84f5-ec838cb0a9b4" />

---

## 📦 Livrables produits

| Type | Description |
|------|--------------|
| **Modèle NLP (Word2Vec)** | Détection automatique de synonymes à partir du corpus métier. |
| **Data Mart Snowflake** | Base sémantique centralisée pour le stockage et la requête des relations. |
| **Application Streamlit** | Interface de validation et d’export pour les Data Stewards. |
| **Exports Collibra Ready** | Fichiers normalisés pour mise à jour du glossaire Collibra. |
| **Documentation technique** | Guide d’utilisation, scripts Python et schémas Snowflake. |

📸 **Image 7 – Export Collibra Ready**

<img width="650" alt="export" src="https://github.com/user-attachments/assets/46f9de30-22b4-4a8f-ae13-c10c734048a1" />

---

## ⚠️ Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **Corpus restreint** | Modèle entraîné uniquement sur un vocabulaire bancaire interne. | Enrichir le corpus avec des textes sectoriels et open data. |
| **Ambiguïté lexicale** | Certains termes polysémiques génèrent de faux positifs. | Ajout d’un module de désambiguïsation contextuelle (spaCy). |
| **Validation manuelle** | Validation humaine nécessaire pour 20 % des suggestions. | Intégration d’un module semi-supervisé d’apprentissage continu. |

📈 **Image 8 – Pipeline NLP simplifié**

<img width="1200" alt="pipeline" src="https://github.com/user-attachments/assets/6e2dcf6e-5b3a-4f7a-b134-5df3e86b77da" />

---

## 💡 Impacts et valeur ajoutée

- **Harmonisation du vocabulaire métier** à l’échelle du groupe.  
- **Amélioration de la recherche Collibra** grâce à la reconnaissance des synonymes.  
- **Gain de productivité** pour les Data Stewards lors de la mise à jour du glossaire.  
- **Réduction des redondances** et incohérences dans la documentation.  
- **Intégration facilitée** des concepts dans la gouvernance globale des données.  

📸 **Image 9 – Vue collaborative Streamlit**

<img width="320" height="200" alt="collaboration" src="https://github.com/user-attachments/assets/e2793f38-0e65-4513-a544-217b2cc94e96" />

---

## 🧠 Enseignements

- Le **traitement sémantique** est un levier puissant pour la gouvernance des données.  
- La **collaboration entre data scientists et métiers** est clé pour la pertinence du modèle.  
- L’intégration du NLP dans la gouvernance ouvre la voie à une **intelligence documentaire continue**.  

---

## 👤 Contact

**Tariq TAMRABET**  
*Data Governance Manager & Data Engineer – Crédit Agricole PFM*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

---

### 🔗 Prochain projet → [Data Quality Dashboard](../data-quality-dashboard/)

---

> *“Structurer le langage des données, c’est renforcer la compréhension des métiers.”*

