# CLASSES.md — Référence des classes CSS utilisées par `/analyse`

Ce document liste toutes les classes CSS utilisées dans `analyse/index.html`. Le HTML est livré sans aucun style ; ce fichier sert de référence pour rédiger le CSS commun ou adapter une feuille existante.

Convention : BEM (Block — Element — Modifier).

---

## Conteneurs racine

| Classe | Élément | Description |
|---|---|---|
| `.report-body` | `<body>` | Conteneur racine pour appliquer un fond de page éventuel et la typographie globale. |
| `.report` | `<main>` | Conteneur principal du rapport (largeur max, marges externes). |

## En-tête du rapport

| Classe | Élément | Description |
|---|---|---|
| `.report__header` | `<header>` | En-tête du document (titre, sous-titre, méta). |
| `.report__eyebrow` | `<p>` | Étiquette de catégorie au-dessus du titre (« Document interne »). |
| `.report__title` | `<h1>` | Titre principal du rapport. |
| `.report__subtitle` | `<p>` | Sous-titre / résumé d'une ligne. |
| `.report__meta` | `<dl>` | Liste de métadonnées (date, périmètre, destinataires). |
| `.report__meta-item` | `<div>` | Une paire label/valeur dans la liste meta. |
| `.report__meta-label` | `<dt>` | Libellé d'une métadonnée. |
| `.report__meta-value` | `<dd>` | Valeur d'une métadonnée. |

## Sommaire

| Classe | Élément | Description |
|---|---|---|
| `.report__nav` | `<nav>` | Bloc de navigation contenant le sommaire. |
| `.report__nav-title` | `<h2>` | Titre du sommaire (« Sommaire »). |
| `.report__nav-list` | `<ol>` | Liste ordonnée des sections. |
| `.report__nav-item` | `<li>` | Entrée du sommaire. |
| `.report__nav-link` | `<a>` | Lien d'ancre vers une section. |

## Sections thématiques

| Classe | Élément | Description |
|---|---|---|
| `.report__section` | `<section>` | Une section thématique du rapport. |
| `.report__section-header` | `<header>` | En-tête d'une section. |
| `.report__section-number` | `<p>` | Numérotation (« Section 1 »). |
| `.report__section-title` | `<h2>` | Titre principal de la section. |
| `.report__section-content` | `<div>` | Conteneur du contenu de la section. |
| `.report__subsection-title` | `<h3>` | Titre de sous-section. |
| `.report__paragraph` | `<p>` | Paragraphe courant du rapport. |
| `.report__paragraph--note` | `<p>` | Variante : paragraphe en note (taille / contraste réduits). |
| `.report__footer` | `<footer>` | Pied de document. |
| `.report__footer-text` | `<p>` | Texte du pied de document. |

## Résumé exécutif — stats grid

| Classe | Élément | Description |
|---|---|---|
| `.summary-stats` | `<ul>` | Grille des stats clés du résumé exécutif. |
| `.summary-stat` | `<li>` | Une carte stat (chiffre + label). |
| `.summary-stat__value` | `<p>` | Valeur chiffrée mise en évidence. |
| `.summary-stat__label` | `<p>` | Libellé court sous la valeur. |

## Effet temps Baltis — graphique en barres animées

| Classe | Élément | Description |
|---|---|---|
| `.baltis-chart` | `<figure>` | Conteneur du graphique. L'attribut `data-baltis-chart` est utilisé par le JS pour l'animation au scroll. La classe `.is-visible` est ajoutée par le JS quand le graphique entre dans le viewport. |
| `.baltis-chart__caption` | `<figcaption>` | Titre du graphique. |
| `.baltis-chart__rows` | `<ol>` | Liste des lignes. |
| `.baltis-chart__row` | `<li>` | Une ligne. La variable CSS inline `--bar-ratio` (0 à 1) pilote la largeur de la barre. |
| `.baltis-chart__label` | `<div>` | Bloc label (date + contexte). |
| `.baltis-chart__date` | `<span>` | Date de sortie. |
| `.baltis-chart__context` | `<span>` | Texte de contexte (mois additionnels, événement). |
| `.baltis-chart__track` | `<div>` | Rail de fond de la barre. |
| `.baltis-chart__fill` | `<div>` | Remplissage proportionnel (animation `transform: scaleX(0 → 1)` quand `.is-visible` est appliqué). |
| `.baltis-chart__amount` | `<div>` | Montant cumulé affiché à droite. |
| `.baltis-chart__note` | `<p>` | Légende sous le graphique. |

## Tableaux de données

| Classe | Élément | Description |
|---|---|---|
| `.data-table` | `<table>` | Tableau de données. |
| `.data-table__caption` | `<caption>` | Légende du tableau. |
| `.data-table__head` | `<thead>` | Bloc d'en-tête de tableau. |
| `.data-table__body` | `<tbody>` | Corps du tableau. |
| `.data-table__row` | `<tr>` | Ligne du tableau. |
| `.data-table__row--total` | `<tr>` | Variante : ligne de total (gras, fond éventuel). |
| `.data-table__row--subtotal` | `<tr>` | Variante : ligne de sous-total. |
| `.data-table__header` | `<th>` | Cellule d'en-tête. |
| `.data-table__header--number` | `<th>` | Variante : en-tête de colonne numérique (aligné à droite). |
| `.data-table__cell` | `<th>` / `<td>` | Cellule de tableau. |
| `.data-table__cell--number` | `<td>` / `<th>` | Variante : cellule numérique (aligner à droite, tabular-nums). |
| `.data-table__cell--total` | `<th>` / `<td>` | Variante : cellule de total (gras). |
| `.data-table__cell--positive` | `<td>` | Variante : montant positif (vert, par exemple). |
| `.data-table__cell--negative` | `<td>` | Variante : montant négatif (rouge, par exemple). |
| `.comparison-table` | `<table>` | Modifieur applicable sur `.data-table` pour le tableau comparatif final. |

## Encadrés (highlight boxes)

| Classe | Élément | Description |
|---|---|---|
| `.highlight-box` | `<aside>` | Encadré pour mettre en avant une information clé. |
| `.highlight-box--neutral` | `<aside>` | Variante : encadré informatif neutre. |
| `.highlight-box--warning` | `<aside>` | Variante : encadré d'alerte (risques, points à surveiller). |
| `.highlight-box__title` | `<h3>` | Titre de l'encadré. |
| `.highlight-box__text` | `<p>` | Paragraphe à l'intérieur de l'encadré. |

## Marqueur « à confirmer » / hypothèse

| Classe | Élément | Description |
|---|---|---|
| `.flag` | `<span>` | Marqueur inline indiquant qu'une donnée est une hypothèse ou doit être confirmée. |

## Listes utilitaires

| Classe | Élément | Description |
|---|---|---|
| `.bullet-list` | `<ul>` | Liste à puces standard du rapport. |
| `.bullet-list__item` | `<li>` | Élément d'une `.bullet-list`. |

## Listes d'informations clé/valeur (contexte)

| Classe | Élément | Description |
|---|---|---|
| `.info-list` | `<dl>` | Liste de descriptions structurée (clé/valeur). |
| `.info-list__item` | `<div>` | Une paire clé/valeur. |
| `.info-list__label` | `<dt>` | Libellé. |
| `.info-list__value` | `<dd>` | Valeur. |

## Frise chronologique

| Classe | Élément | Description |
|---|---|---|
| `.timeline` | `<ol>` | Liste ordonnée des étapes chronologiques. |
| `.timeline__item` | `<li>` | Une étape de la frise. |
| `.timeline__date` | `<p>` | Date de l'étape. |
| `.timeline__event` | `<p>` | Description de l'étape. |

## Avantages / inconvénients

| Classe | Élément | Description |
|---|---|---|
| `.pros-cons` | `<div>` | Conteneur deux colonnes avantages / inconvénients. |
| `.pros-cons__column` | `<div>` | Une colonne. |
| `.pros-cons__column--pros` | `<div>` | Variante : colonne avantages. |
| `.pros-cons__column--cons` | `<div>` | Variante : colonne inconvénients. |
| `.pros-cons__title` | `<h4>` | Titre d'une colonne. |

## Cartes de scénarios (section 10)

| Classe | Élément | Description |
|---|---|---|
| `.scenario-card` | `<article>` | Carte présentant un scénario chiffré. |
| `.scenario-card__header` | `<header>` | En-tête de la carte. |
| `.scenario-card__tag` | `<p>` | Tag du scénario (« Scénario A »). |
| `.scenario-card__title` | `<h3>` | Titre du scénario. |
| `.scenario-card__subtitle` | `<h4>` | Sous-titre (« Hypothèses »). |
| `.scenario-card__body` | `<div>` | Corps de la carte. |
| `.scenario-card__table` | `<table>` | Modifieur applicable sur `.data-table` pour les tableaux de calcul cash internes aux scénarios. |

## Zones d'incertitude (section 12)

| Classe | Élément | Description |
|---|---|---|
| `.uncertainty-list` | `<ol>` | Liste ordonnée des zones d'incertitude. |
| `.uncertainty-list__item` | `<li>` | Un point d'incertitude. |
| `.uncertainty-list__title` | `<h3>` | Titre du point. |
| `.uncertainty-list__text` | `<p>` | Texte explicatif. |

## Bilan annuel (section 7 — sorties / entrées / net)

| Classe | Élément | Description |
|---|---|---|
| `.flow-balance` | `<figure>` | Bloc unifié bilan annuel. |
| `.flow-balance__caption` | `<figcaption>` | Titre du bilan. |
| `.flow-balance__columns` | `<div>` | Conteneur 2 colonnes (sorties / entrées). |
| `.flow-balance__column` | `<section>` | Une colonne. |
| `.flow-balance__column--out` | `<section>` | Variante sorties (terra). |
| `.flow-balance__column--in` | `<section>` | Variante entrées (olive). |
| `.flow-balance__header` | `<header>` | En-tête d'une colonne (libellé + total). |
| `.flow-balance__direction` | `<p>` | Libellé direction (« Sorties » / « Entrées »). |
| `.flow-balance__total` | `<p>` | Total de la colonne. |
| `.flow-balance__total-unit` | `<span>` | Unité « /an ». |
| `.flow-balance__items` | `<ul>` | Liste des postes. |
| `.flow-balance__item` | `<li>` | Un poste (label + valeur). |
| `.flow-balance__item-label` | `<span>` | Libellé du poste. |
| `.flow-balance__item-value` | `<span>` | Valeur chiffrée. |
| `.flow-balance__hint` | `<p>` | Note de bas de colonne. |
| `.flow-balance__net` | `<div>` | Bloc « coût net » sous les colonnes. |
| `.flow-balance__net-row` | `<div>` | Une ligne de coût net. |
| `.flow-balance__net-row--alt` | `<div>` | Variante alternative (après rachat meubles). |
| `.flow-balance__net-label` | `<p>` | Libellé du coût net. |
| `.flow-balance__net-amount` | `<p>` | Conteneur des montants (annuel + mensuel). |
| `.flow-balance__net-value` | `<span>` | Coût annuel. |
| `.flow-balance__net-unit` | `<span>` | Unité « /an ». |
| `.flow-balance__net-monthly` | `<span>` | Coût mensuel équivalent. |
| `.flow-balance__formula` | `<p>` | Rappel de la formule en bas. |

---

## Notes d'intégration

- Les nombres utilisent l'espace insécable (`&nbsp;`) comme séparateur de milliers et la virgule comme séparateur décimal.
- Les cellules numériques portent toutes la classe `.data-table__cell--number` ; appliquer `text-align: right` et `font-variant-numeric: tabular-nums` à cette classe.
- Aucune information critique n'est véhiculée uniquement par la couleur ; les modifieurs `--positive` / `--negative` peuvent être stylés librement, le signe `+`/`−` est déjà présent dans le contenu.
- Le document est imprimable proprement : prévoir `@media print` pour masquer `.report__nav` et casser les pages avant chaque `.report__section` si besoin.
