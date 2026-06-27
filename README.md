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
