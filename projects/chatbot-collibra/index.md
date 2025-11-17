---
layout: project
title: "Chatbot Sémantique Inter-Cloud"
---

# Chatbot Sémantique Inter-Cloud – Crédit Agricole PFM

## Contexte

Dans le cadre du développement du **Thesaurus sémantique** du **Data Management Office (DMO)**, une **mission exploratoire inter-cloud** a été menée pour relier un **chatbot hébergé sur GCP** à une **infrastructure AWS**.  
L’objectif était d’évaluer la faisabilité d’une interaction **cloud-to-cloud sécurisée** permettant au chatbot d’exploiter dynamiquement le **moteur sémantique métier** hébergé sur AWS.

Ce projet s’inscrit dans la stratégie du Crédit Agricole visant à rendre les solutions **d’analyse et de gouvernance de données** accessibles via des interfaces conversationnelles intelligentes.

## Objectif du projet

Mettre en place une **architecture API inter-cloud (GCP ↔ AWS)** permettant à un chatbot d’utiliser le moteur de **Thesaurus sémantique** afin de :
- **Nettoyer, normaliser et reformuler** les requêtes utilisateurs.  
- **Désambigüiser** les termes métier avant exécution par les applications internes.  
- **Renforcer la cohérence sémantique** des échanges entre les environnements cloud.  

L’ambition était de démontrer la faisabilité technique d’une **interopérabilité NLP multi-cloud**, tout en respectant les standards de sécurité du groupe.

## Architecture fonctionnelle

| Composant | Description |
|------------|-------------|
| **Chatbot GCP** | Application hébergée sur Google Cloud (Cloud Run) interrogeant l’API sémantique. |
| **API Gateway AWS** | Point d’entrée REST sécurisé entre GCP et AWS. |
| **Moteur NLP interne (AWS Lambda)** | Traitement sémantique via le Thesaurus : normalisation, désambiguïsation, reformulation. |
| **Base AWS S3 / Logs** | Journalisation des requêtes et résultats d’analyse (requête brute → requête enrichie). |
| **Applications internes** | Consomment la requête reformulée selon les standards métier. |

**Schéma d’architecture du flux inter-cloud :**

<img width="2093" height="313" alt="Untitled diagram-2025-11-14-025553" src="https://github.com/user-attachments/assets/e5483b23-29c8-4ca6-ac9c-1046be19cf37" />



### Prochain projet → [Chatbot Sémantique Inter-Cloud](../chatbot-collibra/)

