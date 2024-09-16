# Secure CI/CD Pipeline

## Description

Ce projet implémente un pipeline CI/CD sécurisé en utilisant GitHub Actions et Jenkins pour automatiser les tests de sécurité à chaque étape du développement. Le pipeline intègre plusieurs outils de sécurité pour analyser les dépendances, détecter les vulnérabilités, effectuer des tests de sécurité statiques et dynamiques, et garantir que les images Docker déployées sont sûres.

### Outils intégrés :
- **Snyk** : Pour détecter les vulnérabilités dans les dépendances Python.
- **Trivy** : Pour scanner les images Docker à la recherche de vulnérabilités.
- **OWASP ZAP** : Pour exécuter des tests d'intrusion automatisés sur l'application.
- **Bandit** : Pour effectuer des analyses statiques de code Python.
- **Dependabot** : Pour surveiller les mises à jour de sécurité des dépendances Python.

## Fonctionnalités

- **Scans automatiques de vulnérabilités** : Analyse des dépendances, du code, et des conteneurs Docker pour détecter des vulnérabilités de sécurité.
- **Analyse statique** : Utilisation de Bandit pour vérifier la sécurité du code Python.
- **Tests d'intrusion automatisés** : OWASP ZAP effectue des tests dynamiques pour évaluer la sécurité de l'application web.
- **Vérification des dépendances** : Dependabot et Snyk identifient et corrigent les dépendances vulnérables.
- **Scan d'images Docker** : Trivy analyse les images Docker pour vérifier leur sécurité.

## Structure du projet

secure-cicd-pipeline/  
├── .github/  
│ └── workflows/  
│     └── ci-pipeline.yml  
├── Jenkinsfile  
├── Dockerfile   
├── requirements.txt  
    └── app/   
        └── main.py  


## Installation

1. **Clonez le dépôt :**

   ```
   git clone https://github.com/votre-utilisateur/secure-cicd-pipeline.git
   cd secure-cicd-pipeline
   ```

2. **Installer les dépendances Python :**

   ```
   pip install -r requirements.txt
   ```

3. **Construire l'image Docker :**

   ```
   docker build -t secure-app .
   ```
   
## Utilisation

### GitHub Actions

Le workflow GitHub Actions est configuré dans .github/workflows/ci-pipeline.yml. Il s'exécute automatiquement lors d'un push ou d'une pull request sur la branche main.

- **Scans des dépendances avec Snyk : Vérifie les vulnérabilités dans requirements.txt.**
- **Analyse statique avec Bandit : Analyse le code Python à la recherche de failles de sécurité.**
- **Scan des images Docker avec Trivy : Vérifie les vulnérabilités dans l'image Docker.**
- **Test d'intrusion avec OWASP ZAP : Exécute des tests de pénétration sur l'application déployée.**

### Jenkins

Le fichier Jenkinsfile décrit les étapes du pipeline dans Jenkins, incluant :

- **Compilation de l'application**
- **Analyse des dépendances et tests de sécurité**
- **Scan d'image Docker**
- **Test d'intrusion automatisé**

### Configuration de Dependabot

Le fichier .github/dependabot.yml configure Dependabot pour vérifier les mises à jour de sécurité des dépendances dans le fichier requirements.txt.

### Contribuer

Les contributions sont les bienvenues ! Veuillez suivre les étapes ci-dessous pour contribuer à ce projet :

1. **Forkez ce dépôt.**
2. **Créez une branche (git checkout -b feature-nouvelle-fonctionnalité).**
3. **Effectuez vos changements et committez-les (git commit -m 'Ajouter nouvelle fonctionnalité').**
4. **Poussez la branche (git push origin feature-nouvelle-fonctionnalité).**
5. **Ouvrez une Pull Request.**
