# CLASSES.md — Référence des classes CSS de `/analyse`

Le HTML est livré sans styles inline. Ce document liste toutes les classes BEM utilisées et leur usage.

---

## Conteneurs racine

| Classe | Élément | Description |
|---|---|---|
| `.report-body` | `<body>` | Fond de page + typographie globale. |
| `.report` | `<main>` | Conteneur principal (largeur max, marges). |

## En-tête du rapport

| Classe | Élément | Description |
|---|---|---|
| `.report__header` | `<header>` | En-tête du document. |
| `.report__eyebrow` | `<p>` | Étiquette catégorie au-dessus du titre. |
| `.report__title` | `<h1>` | Titre principal. |
| `.report__subtitle` | `<p>` | Sous-titre. |
| `.report__meta` | `<dl>` | Métadonnées (date, périmètre, destinataires). |
| `.report__meta-item` | `<div>` | Paire label/valeur. |
| `.report__meta-label` | `<dt>` | Libellé. |
| `.report__meta-value` | `<dd>` | Valeur. |

## Boutons IA (header)

| Classe | Élément | Description |
|---|---|---|
| `.ai-actions` | `<div>` | Bloc « Poser vos questions au dossier » dans le header. |
| `.ai-actions__intro` | `<p>` | Intro courte au-dessus des boutons. |
| `.ai-actions__buttons` | `<div>` | Grille 2 colonnes des 2 boutons (mobile et desktop). |
| `.ai-actions__hint` | `<p>` | Hint sous les boutons sur le presse-papier. |
| `.ai-button` | `<a>` | Bouton individuel (lien externe). |
| `.ai-button__logo` | `<img>` | Logo Cloudinary (22×22 mobile, 32×32 desktop). |
| `.ai-button__title` | `<span>` | Libellé (« Demander à Claude » / « Demander à ChatGPT »). |
| `.ai-toast` | `<div>` | Toast fixe en bas d'écran, position fixed. `.is-visible` est ajouté par JS pendant 4 s après le clic. |

Au clic sur un bouton, le script en pied de page (i) copie le prompt complet dans le presse-papier via `navigator.clipboard.writeText` (avec fallback `document.execCommand('copy')`), (ii) ouvre la conversation dans un nouvel onglet via le `target="_blank"` du lien (l'`href` contient déjà `?q=<prompt>` pour tenter un pré-remplissage automatique), (iii) affiche le toast pour rappeler la possibilité de coller le prompt si la conversation ne s'est pas pré-remplie (cas typique sur l'app mobile ChatGPT qui ne consomme pas le paramètre `?q=`).

## Sommaire

| Classe | Élément | Description |
|---|---|---|
| `.report__nav` | `<nav>` | Bloc sommaire. |
| `.report__nav-title` | `<h2>` | Titre du sommaire. |
| `.report__nav-list` | `<ol>` | Liste ordonnée des sections. |
| `.report__nav-item` | `<li>` | Entrée du sommaire. |
| `.report__nav-link` | `<a>` | Lien d'ancre. |

## Sections

| Classe | Élément | Description |
|---|---|---|
| `.report__section` | `<section>` | Section thématique. |
| `.report__section-header` | `<header>` | En-tête de section. |
| `.report__section-number` | `<p>` | Numéro de section. |
| `.report__section-title` | `<h2>` | Titre de section. |
| `.report__section-content` | `<div>` | Contenu de section. |
| `.report__subsection-title` | `<h3>` | Titre de sous-section. |
| `.report__paragraph` | `<p>` | Paragraphe courant. |
| `.report__paragraph--note` | `<p>` | Variante : paragraphe en note. |
| `.report__footer` | `<footer>` | Pied de document. |
| `.report__footer-text` | `<p>` | Texte du pied. |

## Stats du résumé (section 1)

| Classe | Élément | Description |
|---|---|---|
| `.summary-stats` | `<ul>` | Grille des stats clés. |
| `.summary-stat` | `<li>` | Une carte stat. |
| `.summary-stat__value` | `<p>` | Valeur chiffrée. |
| `.summary-stat__label` | `<p>` | Libellé. |

## Bilan annuel (section 2)

| Classe | Élément | Description |
|---|---|---|
| `.flow-balance` | `<figure>` | Bloc bilan unifié. |
| `.flow-balance__caption` | `<figcaption>` | Titre du bilan. |
| `.flow-balance__columns` | `<div>` | Conteneur 2 colonnes. |
| `.flow-balance__column` | `<section>` | Colonne. |
| `.flow-balance__column--out` | `<section>` | Variante sorties. |
| `.flow-balance__column--in` | `<section>` | Variante entrées. |
| `.flow-balance__header` | `<header>` | En-tête colonne. |
| `.flow-balance__direction` | `<p>` | « Sorties » / « Entrées ». |
| `.flow-balance__total` | `<p>` | Total colonne. |
| `.flow-balance__total-unit` | `<span>` | Unité « /an ». |
| `.flow-balance__items` | `<ul>` | Liste des postes. |
| `.flow-balance__item` | `<li>` | Un poste. |
| `.flow-balance__item-label` | `<span>` | Libellé du poste. |
| `.flow-balance__item-value` | `<span>` | Valeur du poste. |
| `.flow-balance__hint` | `<p>` | Note de bas de colonne. |
| `.flow-balance__net` | `<div>` | Bloc coût net. |
| `.flow-balance__net-row` | `<div>` | Ligne coût net. |
| `.flow-balance__net-row--alt` | `<div>` | Variante (après rachat meubles). |
| `.flow-balance__net-label` | `<p>` | Libellé. |
| `.flow-balance__net-amount` | `<p>` | Conteneur montants. |
| `.flow-balance__net-value` | `<span>` | Coût annuel. |
| `.flow-balance__net-unit` | `<span>` | Unité « /an ». |
| `.flow-balance__net-monthly` | `<span>` | Coût mensuel. |
| `.flow-balance__formula` | `<p>` | Rappel formule. |

## Effet temps Baltis — graphique animé (section 4)

| Classe | Élément | Description |
|---|---|---|
| `.baltis-chart` | `<figure>` | Conteneur. `data-baltis-chart` + classe `.is-visible` ajoutée par JS au scroll. |
| `.baltis-chart__caption` | `<figcaption>` | Titre. |
| `.baltis-chart__rows` | `<ol>` | Liste des lignes. |
| `.baltis-chart__row` | `<li>` | Une ligne. `--bar-ratio` (0-1) pilote la largeur. |
| `.baltis-chart__label` | `<div>` | Label (date + contexte). |
| `.baltis-chart__date` | `<span>` | Date de sortie. |
| `.baltis-chart__context` | `<span>` | Contexte. |
| `.baltis-chart__track` | `<div>` | Rail de fond. |
| `.baltis-chart__fill` | `<div>` | Remplissage animé. |
| `.baltis-chart__amount` | `<div>` | Montant cumulé. |
| `.baltis-chart__note` | `<p>` | Légende. |

## Tableaux

| Classe | Élément | Description |
|---|---|---|
| `.data-table` | `<table>` | Tableau de données. |
| `.data-table__caption` | `<caption>` | Légende. |
| `.data-table__head` | `<thead>` | En-tête. |
| `.data-table__body` | `<tbody>` | Corps. |
| `.data-table__row` | `<tr>` | Ligne. |
| `.data-table__row--total` | `<tr>` | Variante : ligne de total. |
| `.data-table__row--subtotal` | `<tr>` | Variante : ligne de sous-total. |
| `.data-table__header` | `<th>` | Cellule d'en-tête. |
| `.data-table__header--number` | `<th>` | Variante : en-tête numérique (aligné à droite). |
| `.data-table__cell` | `<th>` / `<td>` | Cellule. |
| `.data-table__cell--number` | `<td>` / `<th>` | Variante : cellule numérique. |
| `.data-table__cell--total` | `<th>` / `<td>` | Variante : cellule de total. |
| `.data-table__cell--positive` | `<td>` | Variante : montant positif. |
| `.data-table__cell--negative` | `<td>` | Variante : montant négatif. |
| `.comparison-table` | `<table>` | Modifieur sur `.data-table` pour le comparatif. |

## Encadrés

| Classe | Élément | Description |
|---|---|---|
| `.highlight-box` | `<aside>` | Encadré mise en avant. |
| `.highlight-box--neutral` | `<aside>` | Variante informative. |
| `.highlight-box--warning` | `<aside>` | Variante d'alerte. |
| `.highlight-box__title` | `<h3>` | Titre encadré. |
| `.highlight-box__text` | `<p>` | Paragraphe encadré. |

## Marqueur « à confirmer »

| Classe | Élément | Description |
|---|---|---|
| `.flag` | `<span>` | Marqueur inline pour hypothèse / à confirmer. |

## Listes

| Classe | Élément | Description |
|---|---|---|
| `.bullet-list` | `<ul>` | Liste à puces. |
| `.bullet-list__item` | `<li>` | Élément. |

## Cartes de scénarios (section 5)

| Classe | Élément | Description |
|---|---|---|
| `.scenario-card` | `<article>` | Carte scénario. |
| `.scenario-card__header` | `<header>` | En-tête. |
| `.scenario-card__tag` | `<p>` | Tag (« Scénario A »). |
| `.scenario-card__title` | `<h3>` | Titre. |
| `.scenario-card__body` | `<div>` | Corps. |
| `.scenario-card__table` | `<table>` | Modifieur sur `.data-table` pour les calculs. |

## Zones d'incertitude (section 6)

| Classe | Élément | Description |
|---|---|---|
| `.uncertainty-list` | `<ol>` | Liste numérotée. |
| `.uncertainty-list__item` | `<li>` | Un point. |
| `.uncertainty-list__title` | `<h3>` | Titre. |
| `.uncertainty-list__text` | `<p>` | Texte. |

---

## Notes d'intégration

- Espace insécable comme séparateur de milliers, virgule décimale.
- Cellules numériques alignées à droite via `.data-table__cell--number` + `font-variant-numeric: tabular-nums`.
- Aucune information critique véhiculée uniquement par la couleur ; les signes `+`/`−` sont déjà présents dans le contenu.
- `@media print` masque le sommaire et casse les pages avant chaque section.
- L'animation Baltis respecte `prefers-reduced-motion`.
