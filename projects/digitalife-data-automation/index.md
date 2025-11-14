# Projet Digitalife – Automatisation et fiabilisation des référentiels de données clients

## Contexte


Ce projet a été réalisé au sein de **Digitalife**, entreprise spécialisée dans la transformation digitale des processus commerciaux et administratifs B2B.  
Dans le cadre de la migration vers l’ERP **Odoo**, l’objectif était de **fiabiliser et automatiser les référentiels de données clients et partenaires** afin d’assurer une intégration fluide, conforme et exploitable dans le nouveau système d’information.  

Intégré à l’équipe Data et Transformation, j’ai contribué à concevoir une solution complète de **traitement, enrichissement et normalisation des données** avant leur intégration dans l’ERP.

## Objectif du projet

Mettre en place une solution d’automatisation des flux de données permettant de :
- Nettoyer, enrichir et standardiser les données clients issues de sources externes (BCE, fichiers CSV).  
- Garantir la **qualité, unicité et conformité RGPD** avant l’intégration ERP.  
- Générer des fichiers métiers compatibles avec **Odoo**.  
- Réduire le temps de préparation commerciale et les interventions manuelles.

## Architecture fonctionnelle

| Étape | Description |
|--------|-------------|
| **Extraction** | Collecte des données depuis la BCE et fichiers CSV clients. |
| **Traitement / Nettoyage** | Automatisation via scripts R et Python : suppression doublons, normalisation des formats, contrôle RGPD. |
| **Enrichissement** | Ajout d’informations via API BCE et autres sources partenaires. |
| **Stockage & Suivi** | Base SQL pour journaliser les traitements et suivre les taux de qualité. |
| **Export vers ERP Odoo** | Génération automatique de fichiers d’import au format compatible Odoo. |

**Image 1 – Schéma d’architecture du flux de traitement**

<img width="6302" height="646" alt="Untitled diagram-2025-11-14-015052" src="https://github.com/user-attachments/assets/ab669792-b3c1-42ce-971f-1f526b38b18c" />


**Image 2 – Schéma du data mart des donénes clients importé de la   BCE**
<img width="872" height="375" alt="image" src="https://github.com/user-attachments/assets/4523dfc6-c70b-47f7-b757-be0304fb697c" />

## Stack technique

| Domaine | Outils / Technologies |
|----------|----------------------|
| **Langages** | R, PHP, Python, SQL |
| **Front / Interface Web** | HTML, JavaScript |
| **ERP** | Odoo (scripts d’import Python, champs personnalisés) |
| **Automatisation** | Scripts batch, contrôles qualité, logs |
| **Sources** | API BCE, fichiers CSV |
| **Méthodologie** | Cycle en V – cadrage, développement, tests, intégration |

## Modules fonctionnels

### 1. Application Web de traitement des données
- Interface simple et sécurisée pour le chargement et la vérification des fichiers.  
- Contrôle automatique des formats, unicité, conformité RGPD.  
- Journalisation des opérations et suivi utilisateur.

### 2. Pipeline ETL automatisé
- Nettoyage, enrichissement et transformation des données en scripts R et Python.  
- Insertion dans la base SQL et génération des logs.  
- Calcul des taux de complétude et d’unicité.

### 3. Génération des fichiers ERP
- Production automatique de fichiers d’import au format métier Odoo.  
- Application des règles de structuration internes (clients, fournisseurs, leads).  
- Validation syntaxique avant chargement ERP.

### 4. Tableau de suivi qualité
- Calcul des KPI.
- Visualisation sous forme de rapports internes exportables (CSV ou PDF).

**Image 3 – Interface Web de traitement**

<img width="1069" height="229" alt="image" src="https://github.com/user-attachments/assets/d46b6c14-e194-49e3-a24a-45fc7994355b" />



## Résultats obtenus

| Indicateur | Résultat |
|-------------|-----------|
| **Volume traité** | +100 000 lignes de données par semaine |
| **Gain de temps** | -40 % sur la préparation des fichiers de prospection |
| **Conformité RGPD** | 100 % des référentiels contrôlés et conformes |
| **Automatisation** | Flux de traitement 100 % automatisé de bout en bout |
| **Disponibilité applicative** | Interface accessible et sécurisée via réseau interne |

**Image 3 – Exemple de pipeline de traitement et enrichissement**

<img width="5966" height="595" alt="Untitled diagram-2025-11-14-022749" src="https://github.com/user-attachments/assets/2d8b8c97-fe14-4623-aad4-593ec10d48a3" />


## Livrables produits

| Type | Description |
|------|--------------|
| **Application Web** | Interface HTML/PHP pour le traitement et le suivi des données. |
| **Pipeline ETL** | Scripts R, Python et SQL d’automatisation du flux de données. |
| **Fichiers d’import ERP** | Données prêtes à être intégrées dans Odoo. |
| **Documentation technique** | Règles de transformation, dictionnaire des champs, guide d’intégration. |
| **Tableaux de bord** | Suivi qualité et logs de traitement. |

## Contraintes et pistes d’amélioration

| Limite | Description | Solution envisagée |
|---------|--------------|--------------------|
| **Hétérogénéité des sources** | Formats très variables selon les fichiers d’entrée. | Création d’un module de mapping dynamique des colonnes. |
| **Dépendance aux API externes** | Temps de réponse variables de la BCE. | Mise en place d’un cache local pour limiter les appels. |
| **Interface basique** | Design fonctionnel mais peu ergonomique. | Refonte graphique avec framework frontend moderne. |


## Impacts et valeur ajoutée

- Fiabilisation et centralisation des données clients avant intégration ERP.  
- Réduction des interventions manuelles et des erreurs de saisie.  
- Gain de productivité significatif pour les équipes commerciales.  
- Conformité RGPD garantie sur l’ensemble du référentiel.  
- Amélioration de la gouvernance et de la traçabilité des données.

**Image 5 – Schéma de l’architecture d’automatisation complète**

<img width="752" height="434" alt="Diagramme sans nom drawio" src="https://github.com/user-attachments/assets/70cac2d2-82c1-4509-9d21-2c77b41abf3f" />


## Enseignements

- L’importance d’une **automatisation robuste et documentée** pour garantir la qualité des données avant intégration ERP.  
- La **collaboration entre équipes data et métiers** comme clé de réussite dans les projets de transformation.  
- Une bonne préparation des référentiels assure la **pérennité des systèmes ERP** et la fiabilité des processus de vente et de reporting.

## Contact

**Tariq TAMRABET**  
*Data Developer – Référentiels & Automatisation ERP – Digitalife*  
📧 [tariq.tamrabet@hotmail.com](mailto:tariq.tamrabet@hotmail.com)  
🔗 [LinkedIn](https://linkedin.com/in/tariq-tamrabet)

> *“Des référentiels fiables, c’est le socle d’une transformation digitale réussie.”*


