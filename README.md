# 🍏 Projet SI - Modernisation du Système d'Information du "Verger du Coin"

## ⚠️ Avertissement : Démonstration Technique Locale

> **ATTENTION :** Ce dépôt est conçu pour une **démonstration technique locale** dans le cadre d'une soutenance de projet. Il ne s'agit pas d'un environnement de production.
>
> Les deux composants logiciels majeurs (Dolibarr ERP et le site Web WordPress) sont exécutés dans des conteneurs Docker séparés. **Ils ne sont PAS connectés ni synchronisés entre eux.** Le site WordPress sert uniquement de vitrine fonctionnelle pour illustrer la vision cible des services en ligne.

## 📁 Structure du Dépôt

Le dépôt est organisé autour de deux environnements Docker distincts :
.
├── dolibarr_docker/
│   ├── docker-compose.yml
│   └── dolibarr_volumes.rar
└── wordpress_docker/
     ├── docker-compose.yml
     └── wordpress_volumes.rar

## 🚀 Mise en Place de l'Environnement de Démo

Cet environnement nécessite l'installation préalable de **Docker** et **Docker Compose** (ou Docker Desktop) sur votre machine.

### Prérequis

*   Docker Engine (version 19.03+ recommandée)
*   Docker Compose (version 1.25+ recommandée)
*   Un utilitaire pour extraire les archives au format `.rar` (comme WinRAR, 7-Zip, ou `unrar` sur Linux/macOS).

---

### 1. Dolibarr ERP (Gestion Interne - ERP / CRM Léger)

Cet environnement simule le futur système de gestion interne (pour les stocks, clients fidélité, comptabilité) tel que proposé dans le scénario cible.

#### 1.1. Installation

1.  **Naviguer dans le répertoire Dolibarr :**
    ```bash
    cd dolibarr_docker/
    ```

2.  **Extraction des Volumes Cruciaux :**
    Le fichier `dolibarr_volumes.rar` contient les données initiales du système (base de données pré-remplie, configuration de l'ERP). **Cette étape est obligatoire.**

    **→ Extrayez le contenu de `dolibarr_volumes.rar` directement dans le dossier `dolibarr_docker/`.** L'extraction créera les dossiers nécessaires (ex: `mysql/`, `html/`) qui seront montés par Docker Compose.

3.  **Lancement des Conteneurs :**
    Lancez l'environnement en mode détaché.
    ```bash
    docker-compose up -d
    ```

### 2. WordPress (Site Vitrine & Click & Collect Simulé)

Cet environnement représente le futur site web de l'entreprise, permettant notamment de simuler des parcours clients (réservation de paniers, inscription fidélité en ligne).

#### 2.1. Installation

1.  **Naviguer dans le répertoire WordPress :**
    ```bash
    cd wordpress_docker/
    ```

2.  **Extraction des Volumes Cruciaux :**
    Le fichier `wordpress_volumes.rar` contient l'installation WordPress complète et le thème configuré pour la démo. **Cette étape est obligatoire.**

    **→ Extrayez le contenu de `wordpress_volumes.rar` directement dans le dossier `wordpress_docker/`.** L'extraction créera les dossiers nécessaires (ex: `db/`, `html/`) qui seront montés par Docker Compose.

3.  **Lancement des Conteneurs :**
    Lancez l'environnement en mode détaché.
    ```bash
    docker-compose up -d
    ```

#### 2.2. Accès

Une fois les conteneurs lancés, le site WordPress sera accessible via votre navigateur à l'adresse :

**[http://localhost:80](http://localhost:80)**

---

## 🛑 Arrêt et Nettoyage de l'Environnement

Pour arrêter et supprimer les conteneurs (mais conserver les volumes pour un redémarrage rapide) :

### Arrêt des Conteneurs

Pour chaque environnement, arrêtez les conteneurs :

```bash
# Arrêt de Dolibarr
cd dolibarr_docker/
docker-compose down
# Retour au répertoire racine du projet (optionnel)
cd ..

# Arrêt de WordPress
cd wordpress_docker/
docker-compose down
# Retour au répertoire racine du projet (optionnel)
cd ..
Suppression Complète (Conteneurs et Volumes)

Pour arrêter les conteneurs et supprimer définitivement les volumes (y compris la base de données), utilisez l'option -v (à n'utiliser que si vous souhaitez repartir de zéro et ré-extraire les .rar) :
# Pour Dolibarr
cd dolibarr_docker/
docker-compose down -v

# Pour WordPress
cd wordpress_docker/
docker-compose down -v
