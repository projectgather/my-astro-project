# 02 — Architecture et méthode de travail

Version 0.2 — 2026-10-22

## 1. Principes

- **Le plus simple qui fonctionne.** Chaque dépendance doit répondre à un besoin identifié.
- **Des projets distincts.** Le portfolio présente mon travail ; chaque application possède son propre dépôt et, lorsque c'est pertinent, sa propre démo.
- **Comprendre avant de modifier.** Je dois pouvoir expliquer les principaux choix techniques et vérifier les changements que j'effectue.
- **Vérifier avant de valider.** Une compilation réussie, un test passé et un déploiement fonctionnel sont trois validations différentes.
- **Être transparent.** Je distingue les fonctionnalités terminées, les améliorations en cours et les limites connues.
- **Progresser par étapes.** Je privilégie les modifications ciblées, les tests et les commits explicites plutôt qu'une réécriture globale.

## 2. Vue d'ensemble

```text
Portfolio — Astro
    |
    └── Génération statique
            |
            └── GitHub Pages

AlgoLab — Python
    |
    ├── Interface : Streamlit
    ├── Visualisations : Plotly
    ├── Modules métier : algorithmes et fonctionnalités
    ├── Tests automatisés
    └── Démo : Streamlit Community Cloud
```

Les deux projets sont hébergés dans des dépôts GitHub distincts.

### Portfolio

Le portfolio présente mon profil, mes projets et mes coordonnées. Astro génère le site statique, publié sur GitHub Pages.

- Dépôt : `https://github.com/projectgather/my-astro-project`
- Site : `https://projectgather.github.io/my-astro-project/`

La configuration utilise `site` et `base` dans `astro.config.mjs` pour tenir compte du sous-chemin utilisé par GitHub Pages.

### AlgoLab

AlgoLab est un visualiseur d'algorithmes développé en Python. Streamlit fournit l'interface interactive et Plotly sert aux visualisations.

- Dépôt : `https://github.com/projectgather/algo-lab`
- Démo : `https://algo-labo.streamlit.app/`

Le projet possède son propre README, des modules métier et des fichiers de tests. Leur exécution et leur pertinence doivent être vérifiées séparément.

### Projet complémentaire

Un autre projet pourra être ajouté lorsque le portfolio et AlgoLab auront été consolidés. Son périmètre, sa stack et son architecture seront définis en fonction de son objectif réel.

## 3. Architecture actuelle du portfolio

Le projet utilise Astro, du CSS natif et une configuration destinée à GitHub Pages.

```text
my-astro-project/
├── public/
│   └── cv.pdf
├── src/
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       └── home.css
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

Cette arborescence représente les principaux fichiers identifiés pendant le développement ; elle ne constitue pas nécessairement une liste exhaustive de tous les fichiers du dépôt.

### Responsabilités

- `src/pages/index.astro` : contenu et structure de la page d'accueil.
- `src/styles/home.css` : styles visuels et adaptations aux différentes tailles d'écran.
- `public/` : fichiers servis tels quels par le site, dont le fichier destiné au CV.
- `astro.config.mjs` : configuration d'Astro et paramètres de publication.
- `package.json` : scripts et dépendances du projet.

L'organisation initiale prévoyait plusieurs pages, des composants réutilisables et une collection de projets. L'architecture actuelle est plus simple : ces éléments ne doivent être ajoutés que lorsqu'ils répondent à un besoin réel.

### Choix techniques

| Sujet | Choix actuel | Justification |
|---|---|---|
| Génération du site | Astro | Produire un site statique adapté à un portfolio. |
| Styles | CSS natif | Maîtriser les bases du CSS sans ajouter de dépendance inutile. |
| Hébergement | GitHub Pages | Publier le portfolio à partir du dépôt GitHub. |
| Déploiement | GitHub Actions | Automatiser la publication du site. |
| Contrôle de version | Git et GitHub | Suivre les changements et conserver le code source. |
| Vérification | Build de production et contrôles manuels | Détecter les erreurs de compilation et vérifier le résultat. |

Les audits d'accessibilité, de performance et de navigation restent à effectuer et à documenter avant de tirer des conclusions sur leur qualité.

## 4. Architecture d'AlgoLab

AlgoLab est une application Python organisée autour d'une interface Streamlit et de modules métier.

Les principaux éléments identifiés sont :

```text
visualiseur-algorithmes/
├── app.py
├── algorithmes/
│   ├── tri.py
│   ├── analyse.py
│   ├── defi.py
│   ├── exercices.py
│   ├── entrainement.py
│   ├── experience.py
│   ├── manipulation.py
│   └── progression.py
├── tests/
├── .streamlit/
├── requirements.txt
└── README.md
```

Cette représentation résume les principaux fichiers connus. Elle ne remplace pas l'examen de l'arborescence complète du dépôt.

### Responsabilités principales

- `app.py` : point d'entrée de l'application et interface Streamlit.
- `algorithmes/` : modules qui regroupent différentes fonctionnalités métier.
- `tests/` : tests automatisés du projet.
- `.streamlit/` : configuration et styles liés à Streamlit.
- `requirements.txt` : dépendances Python déclarées.
- `README.md` : présentation du projet, installation, utilisation et limites connues.

Le fichier `app.py` est volumineux. Son découpage éventuel devra être progressif : chaque extraction devra préserver le fonctionnement de l'application et être vérifiée avant d'être validée.

### Choix techniques

| Sujet | Choix actuel | Justification |
|---|---|---|
| Langage | Python | Implémenter les algorithmes et les fonctionnalités métier. |
| Interface | Streamlit | Créer une application interactive sans développer un frontend séparé. |
| Visualisation | Plotly | Représenter graphiquement les données et les étapes pertinentes. |
| Organisation | Modules Python | Séparer une partie de la logique métier de l'interface. |
| Tests | Outils de test Python présents dans le projet | Vérifier les comportements attendus ; l'exécution complète reste à confirmer. |
| Déploiement | Streamlit Community Cloud | Mettre une démonstration en ligne. |

### Sécurité et limites

La sécurité et la persistance des données doivent être considérées dans le contexte de l'hébergement public.

Les points à examiner comprennent notamment :

- la séparation des données entre utilisateurs ;
- la protection des profils et les limites d'un code PIN ;
- la gestion des entrées utilisateur dans le HTML affiché ;
- le comportement du stockage sur la plateforme d'hébergement ;
- la validation des données et la gestion des erreurs.

Les limites effectivement présentes doivent être décrites dans le README et vérifiées dans le code. Une mesure de protection ne doit pas être présentée comme une garantie absolue.

## 5. Git et gestion des versions

Les dépôts utilisent Git pour suivre les changements et GitHub pour héberger le code.

### Règles de travail

1. Consulter `git status` avant de commencer.
2. Lire les modifications avec `git diff`.
3. Effectuer une modification ciblée.
4. Lancer les vérifications adaptées au changement.
5. Corriger les erreurs avant de valider.
6. Créer un commit dont le message décrit précisément le changement.
7. Vérifier le résultat après le déploiement lorsque la modification concerne une application publiée.

Exemples de messages :

```text
docs: actualise le document d'architecture
fix: corrige le lien du CV
test: ajoute un cas de test pour le tri
refactor: extrait une fonction de l'interface
```

La branche principale du dépôt du portfolio est actuellement `master`. Les commandes Git doivent utiliser le nom de branche réellement configuré dans chaque dépôt.

L'objectif est de construire un historique lisible au fil des prochaines modifications, sans fabriquer artificiellement des étapes passées.

## 6. Installation et commandes utiles

L'environnement de développement est déjà installé. Cette section regroupe les commandes courantes plutôt que de répéter la procédure d'installation initiale.

### Portfolio Astro

Depuis le dossier du projet :

```powershell
npm run dev
npm run build
npm run preview
```

- `dev` lance le serveur de développement.
- `build` génère le site de production dans `dist/`.
- `preview` permet de prévisualiser le résultat du build.

Une compilation réussie ne suffit pas à prouver que tous les liens et toutes les fonctionnalités sont corrects en production.

### AlgoLab

Depuis le dossier du projet Python, utiliser l'environnement virtuel du projet lorsqu'il est correctement configuré.

```powershell
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Ces commandes supposent que `python` désigne l'interpréteur de l'environnement virtuel activé. Sinon, il faut employer explicitement le chemin de son exécutable Python.

Les tests doivent être lancés avec l'interpréteur et les dépendances du projet. La commande exacte sera confirmée en fonction de la configuration de test présente dans le dépôt.

## 7. Méthode de travail avec les assistants IA

Les assistants IA peuvent aider à comprendre une erreur, comparer des solutions, rédiger de la documentation ou proposer des modifications. Ils ne remplacent ni l'exécution du code ni la compréhension du résultat.

### Procédure

1. Définir une tâche précise.
2. Fournir le contexte et uniquement les fichiers nécessaires.
3. Demander une explication des changements proposés.
4. Examiner le code avant de l'intégrer.
5. Exécuter les commandes de vérification.
6. Lire les erreurs éventuelles et corriger le problème.
7. Comprendre les modifications avant de créer un commit.
8. Actualiser `docs/04-avancement.md` lorsqu'une étape est réellement terminée.
9. Mettre à jour `docs/skills-evidence.md` uniquement lorsqu'une compétence peut être appuyée par une preuve concrète.

Pour une modification délicate, une seconde revue peut aider à identifier des erreurs ou des risques. Toutefois, une réponse positive d'un assistant ne constitue pas à elle seule une validation technique.

Aucune information confidentielle, aucun secret de déploiement ni aucun contenu de fichier `.env` ne doit être copié dans une conversation.

## 8. Déploiement et vérifications

### Portfolio

Le site est publié sur GitHub Pages avec une URL comportant le sous-chemin `/my-astro-project/`.

Lors de l'ajout de liens vers des ressources du dossier `public/`, il faut tenir compte de cette base. Les chemins absolus écrits en dur peuvent fonctionner localement et être incorrects en production.

Après une modification importante :

- vérifier que le build réussit ;
- vérifier l'état du workflow de déploiement ;
- ouvrir le site publié ;
- contrôler les liens et les ressources modifiés.

### AlgoLab

La démonstration est publiée sur Streamlit Community Cloud. Le comportement de l'application en production doit être vérifié indépendamment de son fonctionnement local.

Il faut notamment documenter les limites du stockage, les éventuelles interruptions de disponibilité et les précautions liées aux données utilisateurs.

## 9. Améliorations prévues

Les priorités actuelles sont :

1. Mettre à jour les documents de cadrage et d'architecture.
2. Vérifier les liens et les ressources du portfolio publié.
3. Préparer des captures d'écran d'AlgoLab et améliorer sa présentation.
4. Vérifier l'exécution et la pertinence des tests.
5. Documenter plusieurs décisions techniques avec mes propres mots.
6. Examiner progressivement le fichier `app.py`.
7. Améliorer la qualité de l'historique Git au fil des modifications.
8. Réaliser des vérifications d'accessibilité et de performance.
9. Réévaluer l'intérêt d'un projet complémentaire après cette consolidation.

**Principe final :** la priorité est de rendre les projets existants compréhensibles, vérifiables et défendables à l'oral avant d'augmenter leur périmètre.
