# 🖥️ GIE Frontend

> Interface graphique JavaFX pour le système de gestion intégré - Gestion des achats et des contacts

[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://www.oracle.com/java/)
[![JavaFX](https://img.shields.io/badge/JavaFX-21-blue.svg)](https://openjfx.io/)
[![Maven](https://img.shields.io/badge/Maven-3.x-red.svg)](https://maven.apache.org/)

---

## 📋 Table des matières

- [À propos](#-à-propos)
- [Technologies utilisées](#-technologies-utilisées)
- [Prérequis](#-prérequis)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Démarrage](#-démarrage)
- [Structure du projet](#-structure-du-projet)

---

## 🎯 À propos

**GIE Frontend** est une application desktop développée en JavaFX qui fournit une interface utilisateur pour gérer les achats et les contacts.

> ⚠️ **Important** : Cette application nécessite le backend GIE pour fonctionner. Le backend doit être lancé avant de démarrer le frontend.

---

## 🛠 Technologies utilisées

| Technologie        | Version   | Description                        |
| ------------------ | --------- | ---------------------------------- |
| **Java**           | 21        | Langage de programmation           |
| **JavaFX**         | 21        | Framework UI                       |
| **Maven**          | 3.x       | Gestion des dépendances            |
| **Gson**           | 2.10.1    | Sérialisation/Désérialisation JSON |
| **OkHttp**         | 4.9.3     | Client HTTP pour REST API          |
| **FontAwesome FX** | 4.7.0-9.1 | Icônes vectorielles                |

---

## 📦 Prérequis

Avant de commencer, assurez-vous d'avoir installé :

- ☕ **JDK 21** - [Télécharger ici](https://www.oracle.com/java/technologies/downloads/#java21)
- 🎨 **JavaFX SDK 22+** - [Télécharger ici](https://gluonhq.com/products/javafx/)
- 📦 **Maven** (3.6+)
- 🌐 **GIE Backend** - Le backend doit être lancé sur `http://localhost:4567`

> ⚠️ **Important** : Ce projet nécessite **JDK 21**. Vérifiez votre version avec `java -version`.

---

## 🚀 Installation

### 1. Cloner le projet

```bash
git clone https://github.com/k2b2gie/gie-frontend.git
cd gie-frontend
```

### 2. Installer les dépendances

```bash
mvn clean install
```

### 3. Compiler et packager le projet

```bash
mvn package
```

Le fichier JAR sera généré dans le dossier `target/` :

- `GieFrontend1-1.0-SNAPSHOT.jar`

---

## ⚙️ Configuration

### Configuration JavaFX

Téléchargez le JavaFX SDK correspondant à votre système depuis [gluonhq.com](https://gluonhq.com/products/javafx/) et extrayez-le dans un dossier de votre choix.

### Configuration Backend

Le backend GIE doit être lancé et accessible sur `http://localhost:4567` avant de démarrer le frontend.

---

## 🎬 Démarrage

### Lancer le backend

D'abord, lancez le backend GIE :

```bash
cd gie-backend
java -jar target/gie-backend-1.0-SNAPSHOT.jar
```

### Lancer le frontend

Remplacez `<CHEMIN_JAVAFX>` par le chemin vers votre JavaFX SDK :

**Windows PowerShell :**

```powershell
java --module-path "C:\chemin\vers\javafx-sdk-22\lib" --add-modules javafx.controls,javafx.fxml -jar .\target\GieFrontend1-1.0-SNAPSHOT.jar
```

**macOS / Linux :**

```bash
java --module-path "/path/to/javafx-sdk-22/lib" --add-modules javafx.controls,javafx.fxml -jar ./target/GieFrontend1-1.0-SNAPSHOT.jar
```

### Alternative : Via Maven Plugin

```bash
mvn clean javafx:run
```

---

## 📁 Structure du projet

```
gie-frontend/
├── src/
│   └── main/
│       ├── java/
│       │   ├── module-info.java                    # Configuration du module Java
│       │   └── com/example/giefrontend1/
│       │       ├── Run.java                        # Point d'entrée de l'application
│       │       ├── Controllers/                    # Contrôleurs JavaFX
│       │       │   ├── LoginController.java
│       │       │   ├── Commercant/                 # Contrôleurs métier
│       │       │   │   ├── AchatController.java    # Gestion des achats
│       │       │   │   ├── CommercantController.java
│       │       │   │   ├── CommercantMenuController.java
│       │       │   │   ├── CreateContactController.java
│       │       │   │   ├── ProduitController.java  # Gestion des produits
│       │       │   │   ├── SearchContactsController.java
│       │       │   │   ├── SearchResultController.java
│       │       │   │   ├── SendEmailController.java
│       │       │   │   └── UpdateContactController.java
│       │       │   └── DTO/                        # Data Transfer Objects
│       │       │       ├── AchatDTO.java
│       │       │       ├── AdresseDTO.java
│       │       │       ├── ContactDTO.java
│       │       │       ├── DetailAchatDTO.java
│       │       │       └── ProduitDTO.java
│       │       ├── Models/                         # Modèles de données
│       │       │   └── Model.java                  # Singleton principal
│       │       ├── Parser/                         # Parseurs JSON
│       │       │   ├── ParserAchat.java
│       │       │   ├── ParserContact.java
│       │       │   └── ParserProduit.java
│       │       └── Views/                          # Gestion des vues
│       │           ├── AccountType.java            # Enum des types de comptes
│       │           ├── AdminMenuOptions.java       # Options du menu
│       │           └── ViewFactory.java            # Factory des vues
│       └── resources/
│           ├── com.example.giefrontend1/
│           │   ├── login.fxml                      # Vue de connexion
│           │   └── Admin/                          # Vues d'administration
│           │       ├── AdminMenu.fxml              # Menu principal
│           │       ├── Contact.fxml
│           │       ├── CreateClient.fxml
│           │       ├── MyPurchases.fxml            # Gestion des achats
│           │       ├── MyPurchasesCreate.fxml
│           │       ├── MyPurchasesDetails.fxml
│           │       ├── MyPurchasesResume.fxml
│           │       ├── MyPurchasesSearch.fxml
│           │       ├── MyPurchasesUpdate.fxml
│           │       ├── SearchContact.fxml
│           │       ├── SearchResults.fxml
│           │       ├── SendEmail.fxml
│           │       ├── Stock.fxml                  # Gestion du stock
│           │       ├── StockCreate.fxml
│           │       ├── StockSearch.fxml
│           │       ├── StockUpdate.fxml
│           │       ├── UpdateClient.fxml
│           │       └── Welcome.fxml
│           └── Style/                              # Feuilles de style CSS
│               ├── AdminMenu.css
│               ├── Clients.css
│               ├── CreateClient.css
│               ├── FindClient.css
│               ├── login.css
│               ├── Purchases.css
│               └── Stock.css
├── pom.xml                                         # Configuration Maven
├── mvnw / mvnw.cmd                                 # Maven Wrapper
└── README.md                                       # Documentation
```

---

## 🐛 Dépannage

### Erreur : "JavaFX runtime components are missing"

Assurez-vous d'avoir téléchargé JavaFX SDK et vérifiez le chemin dans la commande `--module-path`.

### Erreur : Impossible de se connecter au backend

Vérifiez que le backend est démarré sur `http://localhost:4567`.

### Erreur de version Java

Assurez-vous d'utiliser JDK 21 avec `java -version`.

---

## Licence

Ce projet est développé dans le cadre académique pour l'UIASS - EIA.

---

<div align="center">

**[⬆ Retour en haut](#-gie-frontend)**

Made with ☕ and JavaFX

</div>
