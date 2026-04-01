# VitalSync – CI/CD Containerisée

## Description du projet
VitalSync est une application de suivi médical et sportif composée de trois services :
- Un back-end Node.js (API REST)
- Un front-end servi via Nginx
- Une base de données PostgreSQL

L’objectif du projet est de mettre en place une chaîne CI/CD complète avec conteneurisation Docker.

---

## Architecture

- Frontend (Nginx) → sert les fichiers statiques
- Backend (Node.js) → expose une API REST
- Database (PostgreSQL) → stockage des données

Le front communique avec le backend via `/api/`.

---

## Prérequis

Avant de lancer le projet, il est nécessaire d’avoir :
- Docker
- Docker Compose
- Git

---

## Lancer le projet en local

### 1. Cloner le projet
```bash
git clone <URL_DU_REPO>
cd vitalsync
```

### 2. Créer un fichier .env
```bash
POSTGRES_DB=vitalsync
POSTGRES_USER=vitalsync_user
POSTGRES_PASSWORD=strongpassword123
```

### 3. Lancer les conteneurs
```bash
docker-compose up -d
```

### 4. Accéder à l’application
- Frontend : http://localhost:80
- Backend API : http://localhost:3000/api
- Base de données : localhost:5432 (utilisateur: vitalsync_user, mot de passe: strongpassword123)

## CI/CD avec GitHub Actions
Le projet utilise GitHub Actions pour automatiser les tests, la construction et le déploiement
des conteneurs Docker. Les étapes incluent :
1. Linting du code
2. Exécution des tests unitaires
3. Construction des images Docker
4. Déploiement sur un registre Docker (ex: Docker Hub)

## Gestion des secrets
Les informations sensibles (mots de passe, tokens) sont stockées via :
•	un fichier .env en local
•	des secrets GitHub pour la pipeline CI/CD

Cela permet d’éviter toute exposition dans le code source.

## Choix technologiques
	•	Docker : isolation des services et reproductibilité
	•	Docker Compose : orchestration locale simple
	•	Nginx : serveur web + reverse proxy
	•	PostgreSQL : base de données relationnelle robuste
	•	GitHub Actions : intégration CI/CD native
	•	Multi-stage Docker build : optimisation taille et sécurité

⸻
