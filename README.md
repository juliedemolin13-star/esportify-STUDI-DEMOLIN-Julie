# esportify-STUDI-DEMOLIN-Julie
# 🎮 Esportify

Esportify est une plateforme web dédiée à l'organisation et la gestion de tournois e-sport.  
Projet réalisé dans le cadre de l'examen **Développeur Web**.

⚠️ Environnement local

Le projet est conçu pour fonctionner sur un environnement PHP 8 et MySQL 8 (XAMPP ou Laragon).
L’ensemble du code source ainsi que le script de base de données (`database.sql`) sont fournis dans ce dépôt.

---

## 📌 Fonctionnalités prévues
- Page d’accueil avec présentation et événements
- Connexion / inscription utilisateurs
- Rôles utilisateurs :
  - Joueur : inscription aux tournois
  - Organisateur : création/gestion d’événements
  - Administrateur : validation et modération
- Base de données relationnelle (voir `database.sql`)

---

## 📂 Structure du projet

--- index.php
<?php
require_once "config.php"; // connexion base de données

echo "<h1>Bienvenue sur Esportify 🎮</h1>";
echo "<p>Ceci est la page d'accueil de ton projet.</p>";
?>

config.php 
<?php
// Configuration base de données
$host = "localhost";
$dbname = "esportify";
$username = "root";
$password = ""; // mot de passe vide avec Laragon

try {
    $pdo = new PDO("mysql:host=$host;dbname=$dbname;charset=utf8", $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    die("Erreur de connexion à la base de données : " . $e->getMessage());
}
?>

database.sql
-- Création de la base
CREATE DATABASE IF NOT EXISTS esportify CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
USE esportify;

-- Table Utilisateurs
CREATE TABLE utilisateurs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    pseudo VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    mot_de_passe VARCHAR(255) NOT NULL,
    role ENUM('joueur', 'organisateur', 'admin') NOT NULL DEFAULT 'joueur',
    date_creation TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Table Événements
CREATE TABLE evenements (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titre VARCHAR(100) NOT NULL,
    description TEXT,
    nb_joueurs INT,
    date_debut DATETIME,
    date_fin DATETIME,
    statut ENUM('en_attente', 'valide', 'refuse') DEFAULT 'en_attente',
    organisateur_id INT,
    FOREIGN KEY (organisateur_id) REFERENCES utilisateurs(id) ON DELETE CASCADE
);

-- Table Inscriptions
CREATE TABLE inscriptions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    utilisateur_id INT,
    evenement_id INT,
    date_inscription TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (utilisateur_id) REFERENCES utilisateurs(id) ON DELETE CASCADE,
    FOREIGN KEY (evenement_id) REFERENCES evenements(id) ON DELETE CASCADE
);

-- Quelques utilisateurs de test (mots de passe en clair pour l’exemple, mais normalement hashés avec bcrypt)
INSERT INTO utilisateurs (pseudo, email, mot_de_passe, role) VALUES
('Moira', 'moira@mail.com', 'mdp_test1', 'joueur'),
('Leo', 'leo@mail.com', 'mdp_test2', 'joueur'),
('Monique', 'monique@mail.com', 'mdp_test3', 'joueur'),
('Admin', 'admin@esportify.com', 'admin123', 'admin');






🛠️ Problème technique rencontré

Durant la mise en place de mon environnement de développement, j’ai rencontré des difficultés avec Laragon (Apache/MySQL).
Malgré plusieurs tentatives de configuration (changements de ports, réinstallation des services, ajustement des fichiers de configuration), les services MySQL et Apache ne démarraient pas correctement, ce qui a empêché l’exécution locale complète du projet.

Pour contourner ce problème et avancer dans le projet, j’ai :

Rédigé le code PHP du site ainsi que la configuration (config.php).

Généré le fichier database.sql contenant la structure et les données de test.

Préparé tous les livrables attendus (maquettes, charte graphique, documentation).
