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

[Documentation Application DataQualityManagement.html](https://github.com/user-attachments/files/23455552/Documentation.Application.DataQualityManagement.html)
<!DOCTYPE html>
<!-- saved from url=(0091)file://nsprod02/dg_france/300/775/09-R%C3%A9pertoire_Perso/Tariq/DOC%20BCBS/Untitled-1.html -->
<html lang="fr"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Documentation Data Quality Management</title>

    <!-- Google Font -->
    <link href="./Documentation Application DataQualityManagement_files/css2" rel="stylesheet">

    <style>
        /* ---------- RESET & GLOBAL ---------- */
        *{margin:0;padding:0;box-sizing:border-box}
        body{
            font-family:'Inter',sans-serif;
            line-height:1.6;
            color:#2c3e50;
            background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);
            min-height:100vh
        }
        .container{
            max-width:210mm;           /* A4 width */
            margin:0 auto;
            background:#fff;
            box-shadow:0 20px 60px rgba(0,0,0,.1);
            min-height:297mm           /* A4 height */
        }

        /* ---------- HEADER ---------- */
        .header{
            background:linear-gradient(135deg,#2c3e50 0%,#e74c3c 100%);
            color:#fff;
            padding:40px;
            text-align:center;
            position:relative;
            overflow:hidden
        }
        .header::before{
            content:'';
            position:absolute;top:-50%;left:-50%;
            width:200%;height:200%;
            background:url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
            opacity:.3;animation:float 20s ease-in-out infinite
        }
        @keyframes float{0%,100%{transform:translate(0,0) rotate(0)}50%{transform:translate(-20px,-20px) rotate(180deg)}}

        .header h1{font-size:2.8em;font-weight:700;margin-bottom:10px;position:relative;z-index:2;text-shadow:2px 2px 4px rgba(0,0,0,.3)}
        .subtitle{font-size:1.2em;font-weight:300;opacity:.9;position:relative;z-index:2;margin-bottom:20px}
        .version-info{background:rgba(255,255,255,.2);padding:15px;border-radius:10px;margin-top:20px;position:relative;z-index:2}
        .version-info p{margin:5px 0;font-size:.9em}

        /* ---------- CONTENT ---------- */
        .content{padding:40px}

        /* --- Table of contents --- */
        .toc{background:linear-gradient(135deg,#f8f9fa 0%,#e9ecef 100%);padding:30px;border-radius:15px;margin-bottom:40px;border-left:5px solid #e74c3c}
        .toc h2{color:#2c3e50;font-size:1.8em;margin-bottom:20px;display:flex;align-items:center;gap:15px}
        .toc-list{display:grid;grid-template-columns:repeat(auto-fit,minmax(300px,1fr));gap:15px}
        .toc-item{display:flex;align-items:center;padding:10px 15px;background:#fff;border-radius:8px;box-shadow:0 2px 8px rgba(0,0,0,.1);transition:.3s}
        .toc-item:hover{transform:translateX(5px);box-shadow:0 4px 15px rgba(231,76,60,.2)}
        .toc-number{background:#e74c3c;color:#fff;width:25px;height:25px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.8em;font-weight:600;margin-right:12px}

        /* --- Sections --- */
        .section{margin-bottom:40px;background:#fff;border-radius:12px;box-shadow:0 4px 20px rgba(0,0,0,.08);overflow:hidden;transition:.3s}
        .section:hover{transform:translateY(-2px);box-shadow:0 8px 30px rgba(0,0,0,.12)}
        .section-header{background:linear-gradient(135deg,#f8f9fa 0%,#e9ecef 100%);padding:20px 30px;border-left:5px solid #e74c3c}
        .section-header h2{color:#2c3e50;font-size:1.8em;font-weight:600;display:flex;align-items:center;gap:15px}
        .number{background:#e74c3c;color:#fff;width:35px;height:35px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:.9em}
        .section-content{padding:30px}

        /* --- Cards & grids --- */
        .intro-cards,.tech-stack,.module-grid,.roadmap-items{display:grid;gap:25px}
        .intro-cards{grid-template-columns:1fr 1fr}
        .tech-stack{grid-template-columns:repeat(auto-fit,minmax(200px,1fr))}
        .module-grid{grid-template-columns:1fr}
        .roadmap-items{grid-template-columns:repeat(auto-fit,minmax(250px,1fr))}

        .feature-card,.tech-item,.module-card,.practice-item,.roadmap-item{
            padding:25px;border-radius:10px;border:1px solid #e1e8ed;transition:.3s
        }
        .feature-card{background:linear-gradient(135deg,#e74c3c20 0%,#c0392b20 100%)}
        .feature-card:hover{transform:translateY(-3px);box-shadow:0 8px 25px rgba(231,76,60,.15)}
        .tech-item{background:linear-gradient(135deg,#3498db20 0%,#2980b920 100%);border-left:4px solid #3498db;text-align:center}
        .module-card{background:linear-gradient(135deg,#f39c1220 0%,#e67e2220 100%);border-left:4px solid #f39c12}
        .practice-item{background:linear-gradient(135deg,#17a2b820 0%,#148f7720 100%);border-left:4px solid #17a2b8}
        .roadmap-item{background:linear-gradient(135deg,#6f42c120 0%,#5a32a320 100%);border-left:4px solid #6f42c1}
        .roadmap-item:hover{transform:translateY(-2px);box-shadow:0 6px 20px rgba(111,66,193,.15)}

        h4{margin-bottom:12px;font-weight:600}
        .feature-card h4{color:#c0392b}.tech-item h4{color:#2980b9}.module-card h4{color:#e67e22}
        .practice-item h4{color:#148f77}.roadmap-item h4{color:#5a32a3}

        /* --- Tables --- */
        table{width:100%;border-collapse:collapse}
        .app-table,.workflow-table{margin-top:20px;background:#fff;border-radius:8px;overflow:hidden;box-shadow:0 2px 10px rgba(0,0,0,.08)}
        th{padding:15px;text-align:left;font-weight:600;font-size:.9em;color:#fff}
        .app-table th{background:linear-gradient(135deg,#e74c3c 0%,#c0392b 100%)}
        .workflow-table th{background:linear-gradient(135deg,#27ae60 0%,#229954 100%)}
        td{padding:15px;border-bottom:1px solid #ecf0f1;font-size:.9em}
        tr:hover td{background:#f8f9fa}
        .step-number-cell{background:#27ae60;color:#fff;font-weight:700;text-align:center;width:50px}

        /* --- Code blocks & diagrams --- */
        .code-block,.architecture-diagram{
            background:#2c3e50;color:#ecf0f1;padding:25px;border-radius:8px;font-family:'Monaco','Menlo',monospace;font-size:.9em;overflow-x:auto;margin:20px 0;position:relative
        }
        .code-block::before{content:'💻';position:absolute;top:8px;right:15px;opacity:.3;font-size:1.2em}
        .architecture-diagram::before{content:'🏗️ Architecture';top:10px;right:20px;font-size:.8em;opacity:.3;position:absolute}

        /* --- Table-cards grid --- */
        .tables-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(400px,1fr));gap:20px;margin-top:20px}
        .table-card{background:#fff;border:1px solid #e1e8ed;border-radius:10px;overflow:hidden;transition:.3s}
        .table-card:hover{transform:translateY(-3px);box-shadow:0 8px 25px rgba(0,0,0,.1)}
        .table-header{background:linear-gradient(135deg,#9b59b6 0%,#8e44ad 100%);color:#fff;padding:15px 20px;font-weight:600}
        .table-body{padding:20px}
        .columns-list{background:#f8f9fa;padding:10px;border-radius:5px;font-family:'Monaco','Menlo',monospace;font-size:.8em;color:#6c757d}

        /* --- Footer --- */
        .footer{background:#2c3e50;color:#fff;padding:30px;text-align:center;margin-top:40px}
        .footer h3{margin-bottom:10px;font-weight:600}
        .footer p{opacity:.8}

        /* --- Print button --- */
        .print-button{position:fixed;top:20px;right:20px;background:#e74c3c;color:#fff;border:none;padding:12px 24px;border-radius:25px;cursor:pointer;font-weight:600;box-shadow:0 4px 15px rgba(231,76,60,.3);transition:.3s;z-index:1000}
        .print-button:hover{background:#c0392b;transform:translateY(-2px);box-shadow:0 6px 20px rgba(231,76,60,.4)}

        /* --- Responsive & Print --- */
        @media print {.print-button{display:none}body{background:#fff}.container{box-shadow:none}.section{page-break-inside:avoid}}
        @media(max-width:768px){
            .container{margin:0;border-radius:0}
            .header{padding:30px 20px}.content{padding:20px}
            .intro-cards,.best-practices{grid-template-columns:1fr}
            .header h1{font-size:2em}.tables-grid{grid-template-columns:1fr}
        }
    </style>
</head>
<body>

<button class="print-button" onclick="window.print()">📄 Imprimer PDF</button>

<div class="container">
    <!-- ---------- HEADER ---------- -->
    <div class="header">
        <h1>DATA QUALITY MANAGEMENT</h1>
        <p class="subtitle">Portail Streamlit pour la Gestion de la Qualité des Données</p>
        <div class="version-info">
            <p><strong>Version :</strong> 1.0 — Juillet&nbsp;2025</p>
            <p><strong>Auteur :</strong> Équipe DQ&nbsp;/&nbsp;DMO</p>
        </div>
    </div>

    <div class="content">
        <!-- ---------- TABLE DES MATIERES ---------- -->
        <div class="toc">
            <h2>📋 Table des Matières</h2>
            <div class="toc-list">
                <div class="toc-item"><div class="toc-number">1</div><span>Présentation générale</span></div>
                <div class="toc-item"><div class="toc-number">2</div><span>Architecture technique</span></div>
                <div class="toc-item"><div class="toc-number">3</div><span>Prérequis et installation</span></div>
                <div class="toc-item"><div class="toc-number">4</div><span>Lancement de l'application</span></div>
                <div class="toc-item"><div class="toc-number">5</div><span>Parcours fonctionnel</span></div>
                <div class="toc-item"><div class="toc-number">6</div><span>Description des modules</span></div>
                <div class="toc-item"><div class="toc-number">7</div><span>Mapping tables Snowflake</span></div>
                <div class="toc-item"><div class="toc-number">8</div><span>Gestion des erreurs &amp; logs</span></div>
                <div class="toc-item"><div class="toc-number">9</div><span>Sécurité et bonnes pratiques</span></div>
                <div class="toc-item"><div class="toc-number">10</div><span>Roadmap &amp; améliorations</span></div>
            </div>
        </div>

        <!-- ---------- SECTION 1 ---------- -->
        <div class="section">
            <div class="section-header"><h2><span class="number">1</span>Présentation Générale</h2></div>
            <div class="section-content">
                <p>L'application <strong>Data Quality Management</strong> est un portail Streamlit tout‑en‑un qui centralise la gestion de la qualité des données dans l'écosystème Collibra et Snowflake.</p>

                <div class="intro-cards">
                    <div class="feature-card"><h4>📊 Import &amp; Templates</h4><p>Importation de templates Data Quality depuis Excel ou Snowflake avec détection automatique des nouvelles règles et mesures.</p></div>
                    <div class="feature-card"><h4>🏗️ Génération Collibra</h4><p>Création automatique des objets Collibra&nbsp;: Business Terms, Data Elements, Rules et Results prêts à l'import.</p></div>
                    <div class="feature-card"><h4>📈 Historisation</h4><p>Maintien d'un historique complet des exécutions avec tableau de bord intégré sur Snowflake.</p></div>
                    <div class="feature-card"><h4>🔄 Workflow Guidé</h4><p>Processus pas‑à‑pas pour la validation, synchronisation et déploiement des règles de qualité.</p></div>
                </div>

                <h3 style="margin-top:30px;color:#2c3e50">Deux Sous‑Applications</h3>
                <table class="app-table">
                    <thead><tr><th>App</th><th>Nom (menu)</th><th>Finalité principale</th></tr></thead>
                    <tbody>
                        <tr><td><strong>1</strong></td><td><strong>Data Quality Mapping</strong></td><td>Documentation &amp; mapping métier</td></tr>
                        <tr><td><strong>2</strong></td><td><strong>Historisation DQ</strong></td><td>Synchronisation Snowflake pour reporting</td></tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- ---------- SECTION 2 ---------- -->
<div class="section">
            <div class="section-header"><h2><span class="number">2</span>Architecture Technique</h2></div>
            <div class="section-content">
                <div class="architecture-diagram">
<pre>┌──────────────┐  Excel/CSV   ┌──────────────┐
│  Utilisateur │ ───────────▶ │  Streamlit   │
└──────────────┘              │  (Docker)    │
        ▲                     ├──────────────┤
        │ REST/OAuth          │  Python&nbsp;3.11 │
        ▼                     │  pandas      │
┌──────────────┐              │  snowflake   │
│  Snowflake   │ ◀─ JDBC ─────┴──────────────┘
└──────────────┘
</pre>
                </div>

                <div class="tech-stack">
                    <div class="tech-item"><h4>🎨 Front-end</h4><p>Streamlit&nbsp;≥&nbsp;1.33</p></div>
                    <div class="tech-item"><h4>⚙️ Back-end</h4><p>Python&nbsp;3.11, pandas,<br>snowflake-connector</p></div>
                    <div class="tech-item"><h4>🗄️ Base de données</h4><p>Snowflake (privatelink)</p></div>
                    <div class="tech-item"><h4>🔐 Auth</h4><p>OAuth (token dans <code>st.secrets</code>)</p></div>
                </div>
            </div>
        </div>
        <!-- ---------- SECTION 3 ---------- -->
        <div class="section">
            <div class="section-header"><h2><span class="number">3</span>Prérequis et Installation</h2></div>
            <div class="section-content">
                <h4>Environnement Local</h4>
                <div class="code-block">
git clone git@github.com:your-org/data-quality-dmo.git
cd data-quality-dmo
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
                </div>

                <h4>Configuration Snowflake (~/.streamlit/secrets.toml)</h4>
                <div class="code-block">
[snowflake]
account        = "wxcvor-turing.privatelink"
warehouse      = "CEOS_BAS_WH"
role           = "SG-APP-SNOWFLAKE-DATA-MGMT-SO"
oauth_token    = "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiI..."
                </div>
            </div>
        </div>

        <!-- ---------- SECTION 4 ---------- -->
        <div class="section">
            <div class="section-header"><h2><span class="number">4</span>Lancement de l'Application</h2></div>
            <div class="section-content">
                <div class="code-block">
streamlit run APPLI_MANAGEMENT_DQ.py
                </div>
                <p style="margin-top:15px"><em>Par défaut, la page d'accueil affiche deux tuiles&nbsp;: «&nbsp;Data Quality Mapping&nbsp;» (App&nbsp;1) et «&nbsp;Historisation&nbsp;DQ&nbsp;» (App&nbsp;2).</em></p>
            </div>
        </div>

        <!-- ---------- SECTION 5 ---------- -->
        <div class="section">
            <div class="section-header"><h2><span class="number">5</span>Parcours Fonctionnel</h2></div>
            <div class="section-content">
                <h4>App&nbsp;1 – Data&nbsp;Quality&nbsp;Mapping</h4>
                <table class="workflow-table">
                    <thead><tr><th>Étape</th><th>Écran</th><th>Action clé</th><th>Table Snowflake cible</th></tr></thead>
                    <tbody>
                        <tr><td class="step-number-cell">0</td><td>Actualité&nbsp;DQ</td><td>Import template, détection nouvelles règles/mesures</td><td><code>DQ_TEMP_COLLIB2</code></td></tr>
                        <tr><td class="step-number-cell">1</td><td>Association&nbsp;BT ↔&nbsp;Colonnes</td><td>Mapping Business&nbsp;Term</td><td><code>DQ_MAPP_BT</code></td></tr>
                        <tr><td class="step-number-cell">2</td><td>Documentation nouvelles colonnes</td><td>Métadonnées Data&nbsp;Elements</td><td><code>DQ_DATAELEMENT_CREATED</code></td></tr>
                        <tr><td class="step-number-cell">3</td><td>Validation objets Collibra</td><td>Push BT &amp;&nbsp;DE</td><td><code>DQ_BT_CREATED</code>, <code>DQ_DATAELEMENT_CREATED</code></td></tr>
                        <tr><td class="step-number-cell">4</td><td>Validation règles &amp; mesures</td><td>Export templates</td><td>—</td></tr>
                        <tr><td class="step-number-cell">5</td><td>Récupération templates</td><td>Téléchargement</td><td>—</td></tr>
                        <tr><td class="step-number-cell">6</td><td>Réinitialiser&nbsp;BDD</td><td>Purge tables</td><td>—</td></tr>
                    </tbody>
                </table>

                <h4 style="margin-top:30px">App&nbsp;2 – Historisation&nbsp;DQ</h4>
                <div class="module-grid">
                    <div class="module-card"><h4>1.&nbsp;Upload &amp; Validation</h4><p>Upload Rules &amp;&nbsp;Results avec contrôle des colonnes.</p></div>
                    <div class="module-card"><h4>2.&nbsp;Configuration</h4><p>Définir fréquence attendue et statut initial.</p></div>
                    <div class="module-card"><h4>3.&nbsp;Aperçu Final</h4><p>Prévisualisation des tables avant sauvegarde.</p></div>
                    <div class="module-card"><h4>4.&nbsp;Enregistrement Snowflake</h4><p>TRUNCATE + <code>write_pandas</code> vers <code>DQ_RESULTATS_MAITRE</code>, <code>DQ_HISTORIQUE_EXECUTIONS</code>, <code>DQ_TABLEAU_BORD</code>.</p></div>
                </div>
            </div>
        </div>

        <!-- ---------- SECTION 6 ---------- -->
        <div class="section">
            <div class="section-header"><h2><span class="number">6</span>Description des Modules</h2></div>
            <div class="section-content">
                <div class="module-grid">
                    <div class="module-card"><h4>Connexion Snowflake</h4><p>OAuth via rôle <code>SG‑APP‑SNOWFLAKE‑DATA‑MGMT‑SO</code>.</p></div>
                    <div class="module-card"><h4>Génération Rules&nbsp;&amp;&nbsp;Results</h4><p><code>generate_template_regles()</code> &amp; <code>generate_result_table()</code>.</p></div>
                    <div class="module-card"><h4>Build Data&nbsp;Elements</h4><p>Détection + enrichissement des colonnes nouvelles.</p></div>
                    <div class="module-card"><h4>Historisation</h4><p>Calcul retard, UUID exécutions, agrégation mensuelle.</p></div>
                </div>
            </div>
        </div>

       
        <!-- SECTION 7 — Mapping Snowflake (reporting) -->
        <div class="section">
            <div class="section-header"><h2><span class="number">7</span>Mapping des Tables Snowflake</h2></div>
            <div class="section-content">
                <div class="tables-grid">
                    <!-- CARD MAITRE -->
                    <div class="table-card">
                        <div class="table-header">DQ_RESULTATS_MAITRE</div>
                        <div class="table-body">
                            <h5>Rôle</h5><p>Table maître des résultats pour reporting Power BI.</p>
                            <table class="inner-columns">
                                <thead><tr><th>Colonne</th><th>Description</th></tr></thead>
                                <tbody>
                                    <tr><td>ID_RESULTAT</td><td>Clé primaire technique</td></tr>
                                    <tr><td>NOM_RESULTAT</td><td>Full&nbsp;Name du Data&nbsp;Quality&nbsp;Result</td></tr>
                                    <tr><td>REGLE_ASSOCIEE</td><td>Full&nbsp;Name de la règle exécutée</td></tr>
                                    <tr><td>SCORE_QUALITE_ACTUEL</td><td>Score % de la dernière exécution</td></tr>
                                    <tr><td>STATUT_ACTUEL</td><td>Réussi / Échoué</td></tr>
                                    <tr><td>FREQUENCE_ATTENDUE</td><td>Quotidien / Mensuel / Annuel</td></tr>
                                    <tr><td>EST_EN_RETARD</td><td>O / N (calcul automatique)</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- CARD HISTORIQUE -->
                    <div class="table-card">
                        <div class="table-header">DQ_HISTORIQUE_EXECUTIONS</div>
                        <div class="table-body">
                            <h5>Rôle</h5><p>Historique détaillé de chaque exécution de règle.</p>
                            <table class="inner-columns">
                                <thead><tr><th>Colonne</th><th>Description</th></tr></thead>
                                <tbody>
                                    <tr><td>ID_EXECUTION</td><td>UUID d’exécution</td></tr>
                                    <tr><td>ID_RESULTAT</td><td>FK vers <code>DQ_RESULTATS_MAITRE</code></td></tr>
                                    <tr><td>DATE_CHARGEMENT</td><td>Date de chargement (AAAA‑MM‑JJ)</td></tr>
                                    <tr><td>TOTAL_ELEMENTS_MESURES</td><td>Population *100</td></tr>
                                    <tr><td>SCORE_QUALITE</td><td>Score % de cette exécution</td></tr>
                                    <tr><td>STATUT_RESULTAT</td><td>Réussi / Échoué</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- CARD TABLEAU BORD -->
                    <div class="table-card">
                        <div class="table-header">DQ_TABLEAU_BORD</div>
                        <div class="table-body">
                            <h5>Rôle</h5><p>Aggregation mensuelle pour les KPIs de pilotage.</p>
                            <table class="inner-columns">
                                <thead><tr><th>Colonne</th><th>Description</th></tr></thead>
                                <tbody>
                                    <tr><td>DATE_CAPTURE</td><td>Mois de référence (AAAA‑MM‑JJ)</td></tr>
                                    <tr><td>DOMAINE</td><td>Nom du domaine fonctionnel</td></tr>
                                    <tr><td>NOMBRE_CONTROLES</td><td>Nb de résultats actifs</td></tr>
                                    <tr><td>NOMBRE_REUSSIS</td><td>Nb OK</td></tr>
                                    <tr><td>NOMBRE_ECHOUES</td><td>Nb KO</td></tr>
                                    <tr><td>SCORE_QUALITE_MOYEN</td><td>Moyenne pondérée des scores</td></tr>
                                    <tr><td>TENDANCE_HEBDOMADAIRE</td><td>Amélioration / Dégradation</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div><!-- /tables-grid -->
            </div>
        </div>

        <!-- SECTION 8, 9, 10 (inchangés, cf. version précédente) -->
        <div class="section"><div class="section-header"><h2><span class="number">8</span>Gestion des Erreurs &amp; Logs</h2></div>
            <div class="section-content best-practices">
                <div class="practice-item"><h4>Logs Streamlit</h4><p>Affichage <code>st.error()</code> &amp; trace pour debug rapide.</p></div>
                <div class="practice-item"><h4>Logging structuré</h4><p>Pipeline vers Loki/ELK pour les environnements prod.</p></div>
            </div>
        </div>

        <div class="section"><div class="section-header"><h2><span class="number">9</span>Sécurité &amp; Bonnes Pratiques</h2></div>
            <div class="section-content best-practices">
                <div class="practice-item"><h4>Secrets Management</h4><p>Utiliser <code>st.secrets</code> / Azure&nbsp;Key&nbsp;Vault.</p></div>
                <div class="practice-item"><h4>Moindre privilège</h4><p>Rôle Snowflake restreint.</p></div>
                <div class="practice-item"><h4>Double confirmation avant purge</h4><p>Protéger les <code>TRUNCATE</code>.</p></div>
            </div>
        </div>

        <div class="section"><div class="section-header"><h2><span class="number">10</span>Roadmap &amp; Améliorations</h2></div>
            <div class="section-content">
                <div class="roadmap-items">
                    <div class="roadmap-item"><h4>Tests unitaires</h4><p>Couverture <code>pytest</code>.</p></div>
                    <div class="roadmap-item"><h4>CI/CD</h4><p>Flux GitHub&nbsp;Actions → Docker&nbsp;Hub.</p></div>
                    <div class="roadmap-item"><h4>Alerting Teams</h4><p>Webhook KO critique.</p></div>
                    <div class="roadmap-item"><h4>Ag‑Grid &amp; Pagination</h4><p>Meilleure UX pour grands jeux.</p></div>
                </div>
            </div>
        </div>
    </div><!-- /content -->

    <div class="footer">
        <h3>Data Quality Management — Documentation</h3>
        <p>©&nbsp;2025&nbsp;Équipe&nbsp;DQ&nbsp;/&nbsp;DMO.&nbsp;Tous droits réservés.</p>
    </div>
</div><!-- /container -->


</body></html>





