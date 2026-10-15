# 02 : Architecture et méthode de travail

Version 0.1 : 2026-10-15

## 1. Principes
- Le plus simple qui marche. Chaque dépendance doit répondre à « sans elle, que ne puis-je pas faire ? ».
- Un site statique : Astro génère du HTML/CSS à la compilation, 0 JavaScript par défaut.
- Chaque brique doit pouvoir être expliquée par moi à l'oral.

## 2. Vue d'ensemble
```
[portfolio]  Astro (statique)  →  GitHub Pages
     │ liens
     ├──► [visualiseur-algos]  Vite + TypeScript  →  GitHub Pages (dépôt séparé) [H]
     └──► [suivi-candidatures] Vite + TypeScript  →  GitHub Pages (dépôt séparé) [H]
```
Pourquoi des dépôts séparés : chaque projet a son README, son historique et sa démo, ce qui est lisible par un recruteur. Compromis : trois configurations de build à apprendre. Si c'est trop lourd, repli possible : A et C comme pages Astro du portfolio.

## 3. Arborescence du portfolio
```
portfolio/
├─ CONTEXT.md
├─ docs/                      # documents de pilotage (non publiés)
│  ├─ 01-cahier-des-charges.md
│  ├─ 02-architecture.md
│  ├─ 04-avancement.md
│  └─ skills-evidence.md
├─ public/                    # fichiers servis tels quels (favicon, cv.pdf si existant)
├─ src/
│  ├─ content.config.ts       # schéma de la collection « projets »
│  ├─ content/projets/        # 1 fichier .md ou .mdx par projet
│  ├─ layouts/Base.astro      # <html>, <head>, en-tête, pied de page, lien d'évitement
│  ├─ components/             # Header, Footer, ProjectCard, StatusBadge, TraceMotif
│  ├─ pages/
│  │  ├─ index.astro
│  │  ├─ a-propos.astro
│  │  ├─ contact.astro
│  │  ├─ mentions-legales.astro
│  │  ├─ 404.astro
│  │  └─ projets/
│  │     ├─ index.astro
│  │     └─ [slug].astro
│  └─ styles/
│     ├─ tokens.css           # variables : couleurs, espacements, tailles de texte
│     └─ base.css             # reset léger, typographie, focus, mise en page
├─ astro.config.mjs
├─ package.json
└─ tsconfig.json
```
Le fichier de schéma sera généré à l'étape d'installation avec la syntaxe de la version d'Astro installée (elle a changé entre versions : vérifier la doc officielle à ce moment).

## 4. Choix techniques et justification
| Sujet | Choix | Raison |
|-------|-------|--------|
| Génération | Astro statique | HTML pur, rapide, apprend les composants sans framework JS |
| Style | CSS natif + variables CSS | Apprentissage réel du CSS, aucune dépendance |
| Contenu | Collection Markdown validée par schéma | Ajouter un projet = ajouter un fichier ; erreurs détectées au build |
| TypeScript | Léger : schéma de contenu, petites fonctions | Je ne maîtrise que les bases ; il sert surtout dans A et C |
| Polices | Auto-hébergées (paquets Fontsource) [H] | Pas de requête externe, bonne performance, confidentialité |
| Motif visuel | SVG statique en composant `TraceMotif.astro` | Léger, décoratif, `aria-hidden` |
| Déploiement | GitHub Pages via GitHub Actions [H] | Gratuit, documenté pour Astro |
| Qualité | Lighthouse (Chrome DevTools) + extension axe DevTools ou WAVE | Gratuit, aucune dépendance de projet |

**Frontmatter d'un projet (champs prévus)** : `titre`, `resume`, `statut` (prevu | en-cours | termine), `stack` (liste), `depot` (optionnel), `demo` (optionnel), `limites` (obligatoire), `date`.

## 5. Architecture des projets (aperçu, détails à l'étape dédiée)

**A : visualiseur**
```
src/
├─ algorithms/     # fonctions pures : (tableau) → liste de pas  (bubbleSort.ts, …)
├─ player/         # état de lecture : index du pas courant, play/pause, vitesse
├─ ui/             # rendu SVG/DOM, contrôles, zone aria-live
├─ types.ts        # type Step (action, indices, instantané du tableau)
└─ main.ts
```
Idée clé : un algorithme ne dessine rien, il renvoie la liste de ses pas avec un instantané du tableau à chaque pas. Le lecteur se déplace dans cette liste. Avec des instantanés, « pas précédent » est trivial. Limite assumée : taille max 50. Rendu en SVG/DOM, pas en canvas, pour l'accessibilité et la simplicité. Les algorithmes étant des fonctions pures, ils se testent sans navigateur.

**C : suivi de candidatures**
```
src/
├─ model.ts        # type Candidature, statuts, validation
├─ storage.ts      # lecture/écriture localStorage, { version: 1, items: [...] }, export/import
├─ ui/             # formulaire, liste, filtres
└─ main.ts
```
Identifiants via `crypto.randomUUID()`, dates en ISO (`YYYY-MM-DD`). L'import JSON est validé avant d'écraser quoi que ce soit.

## 6. Installation (Windows, une seule fois)
Ouvrir PowerShell (ou le terminal intégré de VS Code : menu Terminal > Nouveau terminal).
```powershell
winget install OpenJS.NodeJS.LTS
winget install Git.Git
```
Fermer puis rouvrir le terminal, puis vérifier :
```powershell
node -v
npm -v
git --version
```
Chaque commande doit afficher un numéro de version. Si `npm` affiche une erreur de « scripts désactivés » :
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```
Identité Git (une fois) :
```powershell
git config --global user.name "Ton Nom"
git config --global user.email "ton-email@exemple.fr"
```
Commandes quotidiennes du portfolio (après installation d'Astro) :
```powershell
npm run dev       # serveur local, http://localhost:4321
npm run build     # génère le site dans dist/ ; doit finir sans erreur
npm run preview   # sert le résultat du build
```

## 7. Git
- Un commit par étape vérifiée, message au format `type: description` (ex. `docs: ajoute le cahier des charges`).
- Branche `main` toujours fonctionnelle. Pour un essai risqué : `git switch -c essai-nom`.
- Avant chaque commit : `git status` et relire `git diff`.

## 8. Workflow avec Claude et ChatGPT gratuits (sans accès à mes fichiers)
L'IA ne voit que ce que je colle. Je suis le « pont » : je copie, j'exécute, je vérifie.

1. **Une conversation = une tâche** (ex. « page Accueil »). Les longues conversations dégradent la qualité et consomment les limites gratuites.
2. **Début de conversation** : coller `CONTEXT.md`, puis la tâche, puis seulement les fichiers utiles (pas tout le projet).
3. **Prompt type** :
```
   [contenu de CONTEXT.md]
   Tâche : <une étape précise de docs/04-avancement.md>.
   Fichiers actuels concernés : <chemin + contenu>.
   Donne : 1) ce que tu vas faire en 3 lignes, 2) chaque fichier complet avec son chemin,
   3) la commande de vérification Windows, 4) le résultat attendu, 5) ce que je dois comprendre.
```
4. **Je colle le code dans VS Code**, je lance la vérification. En cas d'erreur, je renvoie le message d'erreur exact **et** le fichier concerné, jamais « ça ne marche pas ».
5. **Compréhension** : avant de commiter, je dois pouvoir expliquer chaque fichier. Sinon je demande « explique ligne par ligne » et je note l'essentiel.
6. **Double regard** : pour les points délicats (accessibilité, schéma de données, déploiement), je soumets le résultat à l'autre IA avec « relis ce code et signale erreurs, risques et choses inutiles ».
7. **Versions et API** : les IA peuvent connaître des versions anciennes. Pour toute commande d'installation ou de configuration, je recoupe avec la documentation officielle (docs.astro.build, vite.dev, docs.github.com).
8. **Fin de session** : je mets à jour `docs/04-avancement.md` (fait, vérifié, prochaine étape) et `docs/skills-evidence.md` seulement si une preuve réelle existe. Puis commit.
9. **Limite de messages atteinte** : je note l'étape en cours dans 04-avancement.md et je reprends dans l'autre IA avec CONTEXT.md + le fichier en cours.

## 9. Déploiement (aperçu)
Dépôt GitHub nommé `<pseudo>.github.io` → site à `https://<pseudo>.github.io`. Workflow GitHub Actions officiel d'Astro. Pour A et C (dépôts normaux), il faudra définir une URL de base (`/nom-du-depot/`) dans la configuration Vite. Procédure détaillée à l'étape « Mise en ligne », d'après la doc officielle du moment.