# 🎮 Esportify – Plateforme de gestion de tournois e-sport

Projet réalisé dans le cadre de l’examen **Graduate Développeur Web**.

Esportify est une application web permettant l’organisation et la gestion de tournois e-sport.  
Elle propose un système d’authentification, de gestion des rôles et un CRUD complet sur les entités principales (tournois, équipes, utilisateurs).

---

## 🏗️ Architecture technique

### Front-end
- HTML5
- CSS3
- JavaScript (Fetch / interactions dynamiques)

### Back-end
- PHP 8
- PDO (requêtes préparées sécurisées)

### Base de données relationnelle
- MySQL 8
- Script fourni : `database.sql`

---

## 🔐 Sécurité

- Hash des mots de passe via `password_hash()` (bcrypt)
- Requêtes préparées (PDO) contre les injections SQL
- Gestion des sessions sécurisées
- Gestion des rôles : Joueur / Organisateur / Administrateur

---

## 🛠️ Fonctionnalités principales

- Inscription / Connexion utilisateurs
- Gestion des rôles
- Création et gestion de tournois
- Inscription à un tournoi
- Interface administrateur
- Modération et validation
- Filtrage dynamique en JavaScript (asynchrone)

---

## ⚙️ Installation locale

### Prérequis
- PHP 8+
- MySQL 8+
- XAMPP ou Laragon

### Étapes d’installation

1. Cloner le dépôt :


2. Importer le fichier `database.sql` dans MySQL.

3. Configurer les paramètres de connexion à la base de données dans le fichier de configuration.

4. Lancer Apache via XAMPP ou Laragon.

5. Accéder à l’application via :


---

## 🌿 Gestion de version (Git)

Le projet est versionné via Git et hébergé sur GitHub.

Workflow utilisé :
- Branche principale : `principal`
- Branche de développement : `dev`
- Commits structurés avec messages explicites

---

## 🚀 Évolutions possibles

- Conteneurisation via Docker
- Intégration d’une base de données non relationnelle
- API REST complète
- Déploiement cloud

---

## 👩‍💻 Auteur

Julie Demolin  
Projet réalisé dans le cadre de la certification Graduate Développeur Web.
