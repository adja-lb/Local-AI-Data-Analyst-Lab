# 🤖 Local AI Data Science Lab (AI-Lab)

Ce dépôt contient l'infrastructure complète d'un **laboratoire d'IA agentique local**, conçu pour l'analyse de données automatisée et le Knowledge Management (gestion des connaissances). 

L'objectif de ce projet est de faire collaborer une équipe d'agents IA autonomes (**CrewAI**) capables de se connecter à des bases de données relationnelles réelles, d'en extraire des insights business, et de documenter automatiquement les résultats dans un second cerveau (**Obsidian**).

---

## 🏗️ Architecture du Système

L'infrastructure est entièrement conteneurisée et isolée via **Docker**, permettant une communication fluide entre le système d'exploitation hôte et les environnements virtuels Linux.

* **Moteur d'Inférence (Cerveau) :** [Ollama](https://ollama.com/) exécutant localement le modèle **Qwen 2.5 (7B)** optimisé pour le code et le raisonnement logique.
* **Interface Utilisateur (UI) :** [Open WebUI](https://github.com/open-webui/open-webui) pour l'interaction directe et le prototypage rapide avec les LLM.
* **Espace de Travail (Workspace) :** Conteneur Docker basé sur Python 3.11, configuré via VS Code **Dev Containers** pour isoler les dépendances de Data Science (`pandas`, `matplotlib`, `psycopg2`).
* **Base de Données (Source) :** Connexion réseau inter-conteneurs (via un pont Docker externe) vers une base de données **PostgreSQL** (`dvdrental`) hébergée dans un environnement Home-Lab distinct.
* **Réseau Restitué (Mémoire) :** Volume Docker synchronisé en temps réel avec un coffre **Obsidian** (sauvegardé sur iCloud) pour l'archivage automatisé des rapports selon la méthodologie **PARA**.

---

## 👥 L'Équipe d'Agents (Multi-Agent Flow)

Le framework s'appuie sur **CrewAI** pour orchestrer un pipeline séquentiel où chaque agent est spécialisé :

1.  **L'Expert de Données SQL :** Conçoit et valide des requêtes PostgreSQL complexes (jointures multi-tables, agrégations) adaptées à la demande business.
2.  **Le Data Analyst Senior :** Interprète les résultats, calcule les KPI, identifie les patterns comportementaux et formule des recommandations stratégiques.
3.  **Le Directeur de la Documentation :** Structure l'information au format Markdown, applique une hiérarchie visuelle claire et nettoie le livrable pour une intégration fluide dans le système de gestion des connaissances.

---

## 🛠️ Stack Technique & Outils

* **Langages :** Python, SQL
* **Frameworks IA :** CrewAI, LiteLLM / LangChain (Ollama integration)
* **Data Science :** Pandas, Matplotlib, Psycopg2 (PostgreSQL adapter)
* **DevOps & Infra :** Docker, Docker Compose, VS Code Dev Containers, Windows Subsystem for Linux (WSL)
* **Knowledge Management :** Obsidian (Architecture PARA)

---

## 🚀 Comment ça fonctionne ?

1. L'infrastructure globale est lancée en arrière-plan :
   ```bash
   docker compose up -d


# 🗺️ AI-Driven Urban Mobility Analytics Framework

## 📋 Aperçu du Projet

| Métrique / Info | Description |
| :--- | :--- |
| **Description** | Un framework de Data Science modulaire et local qui automatise l'extraction de données de transit (API/SQL) et orchestre un système d'agents intelligents (CrewAI + LLM local) pour générer des notes stratégiques d'urbanisme à destination des décideurs publics. |
| **Stack Technique** | Python 3.11, PostgreSQL, CrewAI, Ollama (Qwen2.5-7B), YAML, Markdown/Obsidian |
| **Architecture** | Pipeline découplé à deux étages : Moteur de calcul agentique + Générateur de rendu visuel via cache |
| **Méthodologie** | Cadrage STAR (Situation, Task, Action, Result), Philosophie de développement épurée (Style CLAUDE.md) |

---

## 🎯 Problématisation Business (Méthode STAR)

### 📌 Situation
Les cabinets de conseil en aménagement et les municipalités manquent d'outils agiles pour corréler les données de mobilité douce en temps réel (flux sportifs, micro-mobilité) avec les besoins réels d'infrastructure de voirie, limitant l'efficacité des investissements publics.

### 🎯 Task
Développer un framework automatisé de bout en bout capable d'extraire des indicateurs de transit géospatiaux, d'isoler les axes routiers saturés ou sous-dimensionnés, et de formuler des recommandations d'infrastructure actionnables sous forme de synthèses exécutives.

### 🛠️ Action
1. **Infrastructure Locale Isolée :** Déploiement d'une stack de calcul souveraine via Docker (PostgreSQL et LLM `qwen2.5:7b` embarqué localement via Ollama sur CPU).
2. **Pipeline Découplé & Cache :** Création d'une architecture Python modulaire (`main.py` CLI) séparant la logique lourde d'extraction/analyse (sauvegardée en JSON avec archivage historique) de la logique de restitution graphique instantanée.
3. **Orchestration Multi-Agents :** Configuration d'une équipe d'agents spécialisés (CrewAI) guidés par des contraintes comportementales strictes de concision et de pertinence (Zéro hallucination).

### 📈 Result
* **Zéro coût de Run :** Inférence 100% locale sans dépendance aux API cloud payantes.
* **Flexibilité Visuelle :** Changement de template et génération de livrables Markdown (Obsidian) en < 0.1 seconde grâce au système de cache (`--cached`), évitant de recalculer la logique métier.
* **Livrables à Forte Valeur Ajoutée :** Production automatique de notes stratégiques intégrant l'analyse critique des limites de données (biais d'échantillonnage) et des feuilles de route futures.

---

## 🏗️ Architecture du Code

Le framework est conçu pour être universel et s'adapter à plusieurs bases de données ou cas d'usage simplement en injectant un nouveau fichier de configuration YAML.

```text
ai-lab-workspace/
├── config/
│   └── urban_mobility.yml  # Accès BDD, définitions et contraintes des agents
├── templates/
│   └── layout_star_urban.txt # Moule visuel au format Markdown (Obsidian)
├── src/
│   ├── __init__.py
│   ├── pipeline.py         # Logique lourde CrewAI + Sauvegarde cache JSON
│   └── renderer.py         # Hydratation instantanée du template choisi
└── main.py                 # Point d'entrée unique de l'application (CLI)
