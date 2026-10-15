# 01 : Cahier des charges

Version 0.1 : 2026-10-15

## 1. Objectif
Un portfolio qui permet à un recruteur, en moins de 30 secondes, de comprendre :
qui je suis, ce que je cherche (alternance dev, rentrée 2027), ce que j'ai réellement fait,
et comment me contacter. Il doit aussi me servir à apprendre (Astro, CSS, TypeScript, déploiement).

## 2. Légende
[V] validé · [H] hypothèse · [D] à décider

## 3. Publics et parcours

**PU1 : Recruteur pressé (mobile, 30 s à 2 min)**
Accueil → comprend profil + recherche → Projets → un projet → Contact.
Succès : il trouve mon e-mail en ≤ 3 clics.

**PU2 : Profil technique (développeur, tuteur potentiel)**
Projets → détail d'un projet → dépôt GitHub → démo en ligne.
Succès : il voit le code, la stack, les limites connues, et peut tester la démo.

**PU3 : Navigation clavier / lecteur d'écran**
Lien d'évitement → menu → contenu, sur toutes les pages, sans souris.
Succès : aucune fonction n'est inaccessible au clavier.

## 4. Exigences transverses (mesurables)
- Performance/Accessibilité/Bonnes pratiques/SEO : Lighthouse mobile ≥ 90 sur chaque page (objectif 95+).
- JavaScript livré par le portfolio : 0 par défaut ; tout JS doit être justifié dans docs/02.
- Responsive : aucun scroll horizontal de 320 px à 1440 px ; test à 320, 768, 1280.
- Contraste texte ≥ 4,5:1 (WCAG AA), y compris l'accent violet sur son fond.
- Navigation clavier complète, focus visible, lien d'évitement, `lang="fr"`, un seul `h1` par page.
- Respect de `prefers-reduced-motion` ; aucune animation n'est nécessaire à la compréhension.
- Texte ≥ 16 px, zoom 200 % sans perte de contenu.
- Images : `alt` pertinent (ou `alt=""` si décoratif), dimensions déclarées, formats légers.
- Honnêteté : chaque projet a un statut exact (Prévu / En cours / Terminé) ; chaque compétence a un niveau et une source (docs/skills-evidence.md).
- Hébergement gratuit, aucun service payant. [V]
- Pas d'analytics, pas de cookies, pas de formulaire. [H]
- Français uniquement. [H]

## 5. Direction artistique [V]
- Fond bleu nuit, surfaces plus claires pour les cartes, texte clair, accent violet discret (liens, focus, détails).
- Typographie soignée : 3 familles maximum (titres, texte, code). Choix exact [D1]. Polices auto-hébergées. [H]
- Motif « traces d'algorithmes » : SVG statique (barres, lignes d'étapes), décoratif, `aria-hidden`, sert de séparateur/en-tête. Pas d'animation au MVP.
- Thème sombre uniquement. [H]
- Pas d'effet décoratif sans fonction (pas de particules, parallaxe, curseur custom).

## 6. Pages et critères d'acceptation

Éléments communs : en-tête (Accueil, Projets, À propos, Contact), lien d'évitement, pied de page (année, lien Mentions légales, lien GitHub).

### P1 : Accueil `/`
Rôle : se présenter en 30 s.
Contenu : nom [D2], « Étudiant en BUT1 Informatique, recherche une alternance en développement (rentrée 2027) », 2-3 phrases honnêtes, deux boutons (Voir les projets / Me contacter), aperçu de 2 projets max avec leur statut.
Critères :
- [ ] La mention « alternance » et « rentrée 2027 » est visible sans scroller à 360×640.
- [ ] Un seul `h1`.
- [ ] Chaque projet affiché a un badge de statut exact et mène à sa page.
- [ ] Aucune phrase n'affirme une compétence absente de skills-evidence.md.
- [ ] Les deux boutons sont atteignables au clavier dans un ordre logique.

### P2 : Projets `/projets`
Contenu : liste des projets issus de la collection Markdown.
Critères :
- [ ] Un projet = un fichier `src/content/projets/*.md` ; ajouter un fichier suffit à l'afficher.
- [ ] Badge de statut, stack, résumé en 1-2 phrases, lien vers la page détail.
- [ ] Si aucun projet n'est « Terminé », la page le dit sans détour (pas de projet fictif).
- [ ] Cartes entièrement navigables au clavier, un seul lien par carte.

### P3 : Détail projet `/projets/[slug]`
Sections : Objectif · Statut · Stack · Fonctionnalités du MVP · Ce qui est reporté · Limites connues · Ce que j'ai appris (uniquement si réel) · Liens (dépôt, démo si elle existe) · Captures.
Critères :
- [ ] Le build échoue si un champ obligatoire du frontmatter manque (schéma de contenu).
- [ ] La section « Limites connues » est obligatoire.
- [ ] Le lien « Démo » n'existe que si la démo est déployée et fonctionne.
- [ ] Aucun chiffre (utilisateurs, performances, etc.) qui n'ait été mesuré et expliqué.
- [ ] Captures avec `alt` descriptif.

### P4 : À propos `/a-propos`
Contenu : parcours (BUT1 Informatique), ce que je cherche, compétences avec niveau et source, lien CV si un CV existe.
Critères :
- [ ] Chaque compétence affiche un niveau (Notions / Pratiqué / Démontré) cohérent avec skills-evidence.md.
- [ ] Niveau « Démontré » = lien vers une preuve publique (dépôt ou démo).
- [ ] Pas de barres de pourcentage ni de notes sur 5.
- [ ] Le lien CV n'apparaît que si le fichier existe.

### P5 : Contact `/contact`
Contenu : e-mail en texte, GitHub, LinkedIn si j'en ai un.
Critères :
- [ ] L'adresse e-mail est écrite en toutes lettres (pas seulement une icône) et cliquable (`mailto:`).
- [ ] Textes de liens explicites (« GitHub : <pseudo> », jamais « cliquez ici »).
- [ ] Aucun formulaire. [H]

### P6 : Mentions légales `/mentions-legales` [D3]
Critères :
- [ ] Contenu validé avant mise en ligne (identité de l'éditeur, hébergeur, absence de cookies).
- [ ] Lien depuis le pied de page.

### P7 : Erreur 404 `/404`
Critères :
- [ ] Message clair, liens vers Accueil et Projets, même mise en page que le reste.

## 7. Projets : MVP et reporté

### Projet A : Visualiseur interactif d'algorithmes
Objectif d'apprentissage : TypeScript, structuration du code, DOM/SVG, tests simples, accessibilité.

**MVP**
- 3 algorithmes de tri : à bulles, par sélection, par insertion (liste finale [D5]).
- Entrée : tableau aléatoire (taille 5 à 50) ou saisie de valeurs.
- Lecture : play/pause, pas suivant, pas précédent, réinitialiser, vitesse réglable.
- Affichage : barres, éléments comparés/échangés mis en évidence (pas seulement par la couleur : aussi forme/étiquette).
- Description textuelle du pas courant (zone `aria-live="polite"`), compteurs de comparaisons et d'échanges.
- Clavier complet ; `prefers-reduced-motion` respecté (pas d'auto-lecture).
- Tests automatisés des algorithmes (Vitest [H]) : le résultat est trié et les pas sont cohérents.
- Démo déployée + README honnête (limites incluses).

**Reporté**
- Algorithmes de recherche, graphes, arbres, pathfinding, tris avancés (fusion, rapide).
- Module d'entraînement (« prédis la prochaine étape », quiz) : v2 de A.
- Comparaison côte à côte de deux algorithmes, partage par URL, saisie de pseudo-code par l'utilisateur.
- Son, mode multijoueur, comptes, statistiques en ligne, version anglaise.

### Projet C : Suivi de candidatures d'alternance
Objectif d'apprentissage : modélisation de données, formulaires, persistance, validation, import/export.

**MVP**
- Créer / modifier / supprimer une candidature : entreprise, poste, lien de l'offre, date de candidature, statut, date de relance, notes.
- Statuts (liste finale [D6]) : à postuler, postulée, relancée, entretien, refusée, offre reçue.
- Liste filtrable par statut et triable par date ; compteur par statut.
- Persistance locale (localStorage) avec version de schéma ; export et import JSON avec validation. [H]
- Message explicite : « tes données restent dans ton navigateur ».
- Démo publique avec uniquement des données d'exemple fictives, clairement étiquetées.
- Clavier complet, formulaires avec labels et messages d'erreur accessibles.

**Reporté**
- Comptes, backend, base de données distante, synchronisation entre appareils.
- Notifications/rappels, envoi d'e-mails, intégration calendrier.
- Kanban en glisser-déposer, statistiques avancées, pièces jointes, import automatique d'offres, IA.

### Projet B autonome
Reporté. Son module d'entraînement est candidat à la v2 de A.

## 8. Hors périmètre du portfolio v0
Blog, thème clair, version anglaise, formulaire de contact, analytics, animations, CMS, nom de domaine payant, framework UI (React, Vue…).

## 9. Registre des décisions
| ID | Décision | Statut |
|----|----------|--------|
| V1 | Direction artistique « Éditorial nuit » | Validé |
| V2 | Astro, CSS natif, Markdown/MDX, TypeScript léger | Validé |
| V3 | Projets A et C ; B reporté, module d'entraînement → A v2 | Validé |
| V4 | Hébergement gratuit ; site honnête, rapide, accessible, responsive ; rien d'inventé | Validé |
| H1 | GitHub Pages + GitHub Actions | Hypothèse |
| H2 | A et C : dépôts séparés, Vite + TS sans framework UI | Hypothèse |
| H3 | C : localStorage + export/import JSON, sans backend | Hypothèse |
| H4 | Thème sombre uniquement | Hypothèse |
| H5 | Pas d'analytics ni de formulaire | Hypothèse |
| H6 | Vitest sur les algorithmes purs de A | Hypothèse |
| H7 | Calendrier : v0 fin 2026, A vers mars 2027, C vers mai 2027 | Hypothèse |
| H8 | Français uniquement | Hypothèse |
| D1 | Polices exactes, valeur du violet (contraste) | À décider (phase design) |
| D2 | Identité publique (nom, photo) | À décider (avant contenu phase 1) |
| D3 | Contenu des mentions légales | À décider (avant mise en ligne) |
| D4 | Licence des dépôts | À décider (avant publication de A) |
| D5 | Liste finale des algorithmes de A | À décider (début phase 2) |
| D6 | Statuts et modèle de données de C | À décider (début phase 3) |

## 10. Définition de « terminé » pour une étape
Le code tourne en local (`npm run dev`), `npm run build` passe sans erreur, les critères d'acceptation concernés sont cochés, le changement est commité, et docs/04-avancement.md est à jour.