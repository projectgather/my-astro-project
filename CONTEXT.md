# CONTEXT : à coller au début de chaque conversation avec une IA

Dernière mise à jour : 2026-10-15

## Qui je suis
Étudiant en BUT1 Informatique (France). Langages vus en cours : Python, SQL, C, HTML.
JavaScript/TypeScript : bases seulement. Aucun projet personnel pour l'instant.
Outils : VS Code, Windows, Claude gratuit, ChatGPT gratuit. Pas d'accès de l'IA à mes fichiers.

## Objectif
Trouver une alternance en développement pour la rentrée 2027 (ouvert à plusieurs types de dev).
Moyen : un portfolio honnête + 2 projets réels (A et C).

## Règles non négociables
1. Rien d'inventé : aucun projet, compétence, chiffre ou résultat qui n'existe pas.
   Une compétence n'est publiée que si elle est dans docs/skills-evidence.md.
2. Je dois comprendre ce que je colle : l'IA explique chaque fichier généré.
3. Peu de dépendances. Toute nouvelle dépendance doit être justifiée.
4. Chaque étape est vérifiable (commande + résultat attendu).
5. Commandes pour Windows (PowerShell) et VS Code.
6. Portfolio : rapide, accessible (WCAG AA visé), responsive (320 px → 1440 px).

## Stack
- Portfolio : Astro, CSS natif, Markdown/MDX, TypeScript léger. [V]
- Projets A et C : Vite + TypeScript sans framework UI, dépôts séparés. [H]
- Hébergement : GitHub Pages. [H]

## Direction artistique [V]
« Éditorial nuit » : bleu nuit, surfaces sombres, texte clair, accent violet discret,
typographie soignée, motif inspiré des traces d'algorithmes (décoratif, statique, aria-hidden).

## Projets
- A (visualiseur d'algorithmes) : MVP = 3 algorithmes de tri, lecture pas à pas. Voir docs/01.
- C (suivi de candidatures) : MVP = CRUD local + filtres + export/import JSON. Voir docs/01.
- B autonome : reporté.

## Décisions
Validées [V], hypothèses [H], à décider [D] : voir docs/01-cahier-des-charges.md §9.

## État actuel
Voir docs/04-avancement.md (je le mets à jour à la fin de chaque session).

## Comment l'IA doit répondre
- Une étape à la fois, petite, avec : but → fichiers concernés (chemins) → code complet → commande de vérification → résultat attendu.
- Si une information manque, faire une hypothèse explicite plutôt que poser 10 questions.
- Signaler tout ce qui peut être obsolète (versions, API) et me dire quoi vérifier dans la doc officielle.
- Ne jamais ajouter de fonctionnalité hors MVP sans me le demander.