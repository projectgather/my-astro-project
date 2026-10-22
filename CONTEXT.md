# CONTEXT — Contexte de travail pour les IA

Dernière mise à jour : 2026-10-22

## 1. Qui je suis

Étudiant en BUT1 Informatique en France. Je prépare ma recherche d'alternance pour la rentrée 2027.

Langages étudiés en cours : Python, SQL, C et HTML. JavaScript/TypeScript : bases.

Environnement de travail : Windows, VS Code, PowerShell, Git et GitHub. J'utilise notamment ChatGPT et Claude pour apprendre, concevoir et améliorer mes projets.

Je souhaite comprendre le code et les décisions techniques, pas simplement copier-coller des solutions.

## 2. Objectif

Construire un portfolio honnête et professionnel pour mes candidatures en alternance informatique en 2027.

Je suis ouvert à plusieurs domaines du développement. Mes projets doivent démontrer progressivement mes compétences réelles, ma capacité à apprendre, à tester et à expliquer mes choix.

**Règle centrale : privilégier des projets fonctionnels, compréhensibles et vérifiables plutôt que multiplier les projets ou les fonctionnalités.**

## 3. Règles non négociables

1. **Honnêteté :** ne jamais inventer de projet, de compétence, de chiffre, de test réussi ou de résultat.
2. **Compétences démontrables :** toute compétence présentée publiquement doit être appuyée par des éléments concrets, notamment dans `docs/skills-evidence.md`.
3. **Compréhension :** expliquer le rôle des fichiers, les choix techniques et les changements importants à un niveau adapté à un étudiant de BUT Informatique.
4. **Progression prudente :** procéder par petites étapes vérifiables, sans casser ce qui fonctionne.
5. **Dépendances :** éviter les dépendances inutiles. Justifier toute nouvelle dépendance avant de l'ajouter.
6. **Vérification :** donner les commandes adaptées à Windows/PowerShell et expliquer le résultat attendu. Ne jamais prétendre avoir exécuté un test ou consulté un fichier sans l'avoir réellement fait.
7. **Périmètre :** ne pas ajouter de fonctionnalités importantes en dehors des objectifs définis sans me demander mon accord.
8. **Sécurité :** ne jamais demander de publier des secrets, mots de passe, jetons ou le contenu d'un fichier `.env`.
9. **Qualité web :** préserver le responsive, l'accessibilité et la lisibilité. Viser WCAG 2.2 niveau AA lorsque cela est pertinent.
10. **Respect de l'existant :** examiner l'architecture actuelle avant de proposer une refonte. Ne pas reconstruire un projet qui fonctionne simplement pour changer de technologie.

## 4. Projets et technologies actuels

### Projet 1 — Portfolio

- Technologie : Astro, CSS natif et JavaScript/TypeScript léger lorsque nécessaire.
- Hébergement : GitHub Pages.
- Dépôt : https://github.com/projectgather/my-astro-project
- Site : https://projectgather.github.io/my-astro-project/

Le site possède une première page réalisée et publiée. Son évolution doit se faire progressivement, en conservant le travail déjà validé.

Fichiers importants :
- `src/pages/index.astro` : page d'accueil.
- `src/styles/home.css` : styles de la page d'accueil.
- `astro.config.mjs` : configuration Astro, notamment le sous-chemin de déploiement.
- `public/` : ressources statiques, dont le fichier prévu pour le CV.

Le chemin du lien vers le CV est adapté au déploiement. **Le CV lui-même reste à finaliser : ne pas présenter le document comme prêt tant que son contenu n'a pas été vérifié.**

Direction artistique à préserver : esthétique éditoriale sombre, bleu nuit, surfaces foncées, texte clair, accent violet discret, typographie soignée et références graphiques aux traces d'algorithmes. Ne pas modifier radicalement le design sans demande.

### Projet 2 — AlgoLab, visualiseur d'algorithmes

- Technologies : Python, Streamlit et Plotly.
- Dépôt : https://github.com/projectgather/algo-lab
- Démonstration : https://algo-labo.streamlit.app/

Le projet existe, est développé et dispose d'une démonstration en ligne. Il ne s'agit plus d'un simple projet envisagé.

Il comporte notamment :
- `app.py` : interface et orchestration de l'application.
- `algorithmes/` : modules consacrés aux algorithmes et aux fonctionnalités associées.
- `tests/` : tests automatisés.
- `.streamlit/` : configuration et styles de l'application.
- `requirements.txt` : dépendances Python.

L'application s'est étoffée au fil du développement. Avant toute refonte, examiner le code réel, les tests, l'architecture et le comportement actuel.

Priorités : consolider la qualité, vérifier les algorithmes et les tests, documenter les choix techniques, examiner la sécurité et la persistance des données, puis envisager une refactorisation progressive si elle est justifiée.

Ne pas affirmer que toutes ces vérifications sont terminées sans preuves.

### Projets futurs

Un éventuel projet complémentaire pourra être choisi lorsque les projets existants auront été suffisamment consolidés.

Le suivi de candidatures, précédemment envisagé comme un projet en Vite + TypeScript, reste une idée à réévaluer. Ne pas le considérer comme un projet déjà réalisé ni imposer cette ancienne architecture.

## 5. Organisation et Git

Les projets possèdent des dépôts séparés. Respecter leur organisation actuelle.

Avant une modification importante :
1. Vérifier le dépôt et la branche courante.
2. Consulter l'état Git.
3. Identifier les fichiers concernés.
4. Faire une modification limitée.
5. Exécuter les vérifications adaptées.
6. Examiner le diff avant de créer un commit.

Commandes utiles :

```powershell
git status
git diff --check
git diff
```

Ne pas inventer de commits ou réécrire l'historique pour donner une impression artificielle de progression.

## 6. Documentation du portfolio

Les documents de référence sont notamment :
- `docs/01-cahier-des-charges.md` : objectifs et périmètre.
- `docs/02-architecture.md` : architecture réelle et choix techniques.
- `docs/04-avancement.md` : état du projet et prochaines étapes.
- `docs/skills-evidence.md` : preuves associées aux compétences.

Ces documents doivent correspondre aux projets réellement existants. En cas de contradiction, identifier le point à vérifier avant de modifier ou de présenter une information comme certaine.

## 7. Priorités générales

1. Maintenir le portfolio fonctionnel et vérifier ses liens publiés.
2. Consolider AlgoLab et vérifier les fonctionnalités, les algorithmes et les tests.
3. Documenter les décisions techniques et les difficultés réellement résolues.
4. Améliorer progressivement l'accessibilité, le responsive et la qualité du code.
5. Finaliser le CV et préparer des preuves concrètes pour les candidatures en alternance.
6. Choisir d'éventuels nouveaux projets uniquement lorsqu'ils apportent une réelle valeur ajoutée.

L'état détaillé et les tâches terminées doivent être consultés dans `docs/04-avancement.md`.

## 8. Comment l'IA doit répondre

Pour chaque tâche technique, avancer étape par étape.

Présenter :
1. **But :** ce que l'on cherche à obtenir.
2. **Fichiers concernés :** chemins précis.
3. **Modification :** code complet du fichier si nécessaire, ou modification ciblée clairement indiquée.
4. **Explication :** pourquoi le changement est nécessaire et comment il fonctionne.
5. **Vérification :** commandes PowerShell à exécuter.
6. **Résultat attendu :** comment reconnaître une réussite et quoi faire en cas d'erreur.

Ne pas supposer que l'IA a accès au disque local ou au dépôt : vérifier les fichiers disponibles et demander uniquement les éléments nécessaires lorsque l'accès manque.

Si une information manque, formuler une hypothèse explicite ou poser une question ciblée.

Pour les versions, API et fonctionnalités susceptibles d'évoluer, vérifier la documentation officielle lorsque c'est nécessaire.

**Principe final : préserver ce qui fonctionne, expliquer ce qui change et ne déclarer terminé que ce qui a été vérifié.**