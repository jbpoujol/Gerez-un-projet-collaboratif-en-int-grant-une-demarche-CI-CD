# BobApp - Documentation CI/CD

## Pipeline CI/CD

### 1. Tests Automatisés
Les tests sont exécutés automatiquement sur chaque Pull Request vers la branche `main`.

#### Frontend (Angular)
- Exécution des tests unitaires avec Karma
- Génération des rapports de couverture au format LCOV
- Validation que les tests passent avant le merge

#### Backend (Spring Boot)
- Exécution des tests unitaires avec JUnit
- Génération des rapports de couverture avec JaCoCo
- Validation que les tests passent avant le merge

### 2. Analyse de Code (SonarCloud)
L'analyse de qualité du code est effectuée après chaque merge sur `main`.

- Analyse de la qualité du code
- Mesure de la couverture de tests
- Détection des vulnérabilités
- Identification des duplications de code

### 3. Conteneurisation (Docker)
Les images Docker sont construites et publiées sur Docker Hub après chaque merge sur `main`.

- Construction de l'image frontend (nginx + build Angular)
- Construction de l'image backend (JDK 11 + Spring Boot)
- Publication automatique sur Docker Hub

## KPIs et Objectifs

### 1. Couverture de Code
- **Objectif** : Minimum 80% de couverture
- **Actuel** : 41.4%
- **Plan d'action** : 
  - Identifier les composants critiques non testés
  - Prioriser l'écriture de tests pour ces composants
  - Former l'équipe aux bonnes pratiques de test

### 2. Dette Technique
- **Objectif** : Maximum 5 jours de dette technique
- **Actuel** : 12 problèmes de maintenabilité identifiés
- **Plan d'action** :
  - Résoudre les "code smells" critiques
  - Mettre en place des revues de code systématiques
  - Automatiser la détection des problèmes de qualité

## Métriques Actuelles

### Qualité du Code (SonarCloud)
- **Couverture** : 41.4% (66 lignes à couvrir)
- **Fiabilité** : 1 bug détecté
- **Sécurité** : 0 vulnérabilité
- **Maintenabilité** : 12 "code smells"
- **Duplication** : 0% de code dupliqué

### Performance des Pipelines
- Tests Frontend : ~2 minutes
- Tests Backend : ~3 minutes
- Analyse SonarCloud : ~5 minutes
- Build et Push Docker : ~4 minutes

## Recommandations

1. **Priorité Haute**
   - Augmenter la couverture de tests (objectif : 80%)
   - Résoudre le bug de fiabilité détecté
   - Mettre en place des tests d'intégration

2. **Priorité Moyenne**
   - Optimiser les temps de build Docker
   - Ajouter des tests de performance
   - Mettre en place des métriques de performance applicative

3. **Priorité Basse**
   - Documenter les scénarios de test
   - Optimiser la taille des images Docker
   - Ajouter des tests de sécurité

## Notes et Avis

### Points Positifs
- Pipeline CI/CD fonctionnelle et automatisée
- Intégration réussie avec SonarCloud
- Images Docker disponibles sur Docker Hub

### Points d'Amélioration
- Couverture de tests insuffisante
- Temps de build à optimiser
- Documentation des tests à améliorer

## Installation et Utilisation

## Front-end 

Go inside folder the front folder:

> cd front

Install dependencies:

> npm install

Launch Front-end:

> npm run start;

### Docker

Build the container:

> docker build -t bobapp-front .  

Start the container:

> docker run -p 8080:8080 --name bobapp-front -d bobapp-front

## Back-end

Go inside folder the back folder:

> cd back

Install dependencies:

> mvn clean install

Launch Back-end:

>  mvn spring-boot:run

Launch the tests:

> mvn clean install

### Docker

Build the container:

> docker build -t bobapp-back .  

Start the container:

> docker run -p 8080:8080 --name bobapp-back -d bobapp-back 
