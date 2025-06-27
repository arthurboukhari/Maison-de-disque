# 🎵 Maison de Disque - API de Gestion Musicale

[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.3-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Gradle](https://img.shields.io/badge/Gradle-8.14.2-blue.svg)](https://gradle.org/)
[![H2 Database](https://img.shields.io/badge/Database-H2%20%7C%20MySQL-yellow.svg)](http://www.h2database.com/)
[![License](https://img.shields.io/badge/License-MIT-red.svg)](LICENSE)

## 📋 Description

**Maison de Disque** est une API REST moderne conçue pour la gestion complète d'un label musical. Elle permet de gérer les artistes, albums, tracks, playlists et utilisateurs avec un système d'authentification sécurisé et une intégration d'intelligence artificielle pour enrichir l'expérience musicale.

## ✨ Fonctionnalités

### 🎤 Gestion Musicale
- **Artistes** : Création, modification et gestion des profils d'artistes
- **Albums** : Organisation des collections musicales par artiste
- **Tracks** : Gestion détaillée des morceaux avec genres et durées
- **Playlists** : Création de listes de lecture personnalisées

### 🔐 Authentification & Sécurité
- Authentification JWT sécurisée
- Système de rôles (USER, ADMIN, ARTIST, PRODUCER)
- Endpoints protégés avec Spring Security
- Gestion des sessions utilisateur

### 🤖 Intelligence Artificielle
- Intégration **Mistral AI** pour l'enrichissement du contenu
- Recommandations musicales intelligentes
- Analyse automatique des préférences

### 📚 Documentation API
- Documentation interactive avec **Swagger UI**
- API REST complète et bien documentée
- Endpoints OpenAPI 3.0

## 🏗️ Architecture

```
src/
├── main/
│   ├── java/com/label/
│   │   ├── auth/                 # Authentification JWT
│   │   ├── config/              # Configuration (Security, JWT, OpenAPI)
│   │   ├── entities/            # Modèles de données (JPA)
│   │   └── MaisonDeDisqueApplication.java
│   └── resources/
│       ├── application.yaml     # Configuration principale
│       └── static/              # Ressources statiques
└── test/                        # Tests unitaires
```

### 🗄️ Modèle de Données

- **User** : Utilisateurs avec rôles multiples
- **Artist** : Profils d'artistes avec biographies
- **Album** : Collections d'œuvres musicales
- **Track** : Morceaux individuels avec métadonnées
- **Genre** : Classification musicale
- **Playlist** : Listes de lecture personnalisées

## 🚀 Installation & Démarrage

### Prérequis
- **Java 17** ou supérieur
- **Gradle 8.14.2** (inclus via wrapper)
- **Git**

### 1. Cloner le Projet
```bash
git clone https://github.com/votre-username/Maison-de-disque.git
cd Maison-de-disque
```

### 2. Configuration
Créez un fichier `.env` ou configurez les variables d'environnement :
```bash
MISTRAL_API_KEY=votre-clé-mistral-ai
JWT_SECRET=votre-secret-jwt-super-sécurisé
```

### 3. Lancer l'Application

#### Windows
```bash
./gradlew.bat bootRun
```

#### Linux/macOS
```bash
./gradlew bootRun
```

### 4. Accéder à l'Application
- **API** : http://localhost:8080
- **Swagger UI** : http://localhost:8080/swagger-ui.html
- **Console H2** : http://localhost:8080/h2-console

## 🔧 Utilisation de l'API

### Authentification

#### Inscription
```http
POST /auth/register
Content-Type: application/json

{
  "username": "artist_name",
  "password": "secure_password",
  "email": "artist@example.com",
  "roles": ["ARTIST"]
}
```

#### Connexion
```http
POST /auth/login
Content-Type: application/json

{
  "username": "artist_name",
  "password": "secure_password"
}
```

### Exemples d'Utilisation

#### Récupérer le Token
```bash
curl -X POST http://localhost:8080/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"admin","password":"admin123"}'
```

#### Accéder aux Endpoints Protégés
```bash
curl -X GET http://localhost:8080/api/artists \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

## 🛠️ Technologies Utilisées

### Backend
- **Spring Boot 3.5.3** - Framework principal
- **Spring Security** - Authentification et autorisation
- **Spring Data JPA** - Persistance des données
- **JWT (JSON Web Tokens)** - Authentification stateless

### Base de Données
- **H2 Database** - Base de données en mémoire (développement)
- **MySQL** - Base de données de production (optionnel)

### IA & Documentation
- **Mistral AI** - Intelligence artificielle
- **Swagger/OpenAPI 3** - Documentation API

### Build & Deployment
- **Gradle** - Gestionnaire de build
- **Spring Boot Actuator** - Monitoring

## 📊 Base de Données

### Configuration H2 (Développement)
```yaml
spring:
  datasource:
    url: jdbc:h2:mem:recordlabeldb
    username: sa
    password: password
```

### Console H2
- URL : `http://localhost:8080/h2-console`
- JDBC URL : `jdbc:h2:mem:recordlabeldb`
- Username : `sa`
- Password : `password`

## 🧪 Tests

### Lancer les Tests
```bash
./gradlew test
```

### Rapport de Tests
Les rapports sont générés dans `build/reports/tests/test/index.html`

## 🔒 Sécurité

- **JWT Tokens** avec expiration (24h par défaut)
- **Mots de passe hachés** avec BCrypt
- **CORS configuré** pour les applications frontend
- **Endpoints sécurisés** par rôles utilisateur

## 📈 Monitoring

L'application inclut Spring Boot Actuator pour le monitoring :
- **Health Check** : `/actuator/health`
- **Métriques** : `/actuator/metrics`
- **Info** : `/actuator/info`

## 🤝 Contribution

1. Fork le projet
2. Créez votre branche feature (`git checkout -b feature/AmazingFeature`)
3. Commit vos changements (`git commit -m 'Add some AmazingFeature'`)
4. Push vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrez une Pull Request

## 📝 Roadmap

- [ ] Interface web React/Vue.js
- [ ] API de streaming audio
- [ ] Système de notation et reviews
- [ ] Intégration réseaux sociaux
- [ ] Analytics avancées avec IA
- [ ] Support multi-langues
- [ ] API de recommandations personnalisées

## 🆘 Support

Si vous rencontrez des problèmes :

1. Consultez la [documentation Swagger](http://localhost:8080/swagger-ui.html)
2. Vérifiez les logs de l'application
3. Ouvrez une issue sur GitHub

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 👥 Auteurs

- **Arthur** - *Développeur Principal* - [GitHub](https://github.com/votre-username)

## 🙏 Remerciements

- Spring Boot Team pour le framework extraordinaire
- Mistral AI pour l'intégration d'intelligence artificielle
- La communauté open source pour les outils et libraries

---

<div align="center">
  <p>Made with ❤️ for music lovers</p>
  <p>🎵 "Where code meets melody" 🎵</p>
</div>