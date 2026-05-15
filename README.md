# Landing — 3 rue Fenouillet, Hyères

Landing page privée pour un appartement de 87,61 m² Loi Carrez avec jardin de
130 m², au centre de Hyères. Document envoyé par lien direct à un couple de
prospects après contre-visite.

## Stack

HTML statique pur (CSS + JS inline dans `index.html`). Aucune dépendance npm,
aucune requête réseau externe. La page doit s'ouvrir offline une fois les
assets téléchargés.

## Structure

```
/
├── index.html              # Mono-fichier (HTML + CSS + JS inline)
├── README.md
├── vercel.json             # Cache headers + noindex
├── .gitignore
└── assets/
    ├── fonts/              # .woff2 locaux (Cormorant Garamond + Source Sans 3)
    ├── photos/             # .webp + fallback .jpg
    ├── pdfs/               # diagnostics + accord vis-à-vis
    └── plan.svg            # plan interactif (intégré inline dans index.html)
```

## Déploiement sur Vercel

1. **Pousser le repo sur GitHub.**
   ```bash
   git push -u origin main
   ```
2. **Importer dans Vercel.** Aller sur https://vercel.com → *Add New* →
   *Project* → *Import Git Repository* → sélectionner le repo. Vercel détecte
   le projet statique automatiquement (Framework Preset = *Other*, Build
   Command = vide, Output Directory = vide). *Deploy*.
3. **URL publique.** Vercel attribue une URL `*.vercel.app`. C'est le lien à
   envoyer au prospect.
4. **Domaine personnalisé** (optionnel). *Settings → Domains* → ajouter le
   domaine. Suivre les instructions DNS.

## Édition

Toutes les valeurs textuelles et les chiffres sont en clair dans
`index.html`. Les sections sont commentées avec leur numéro (`01 — HERO`,
`02 — SOMMAIRE`, etc.) pour s'y retrouver rapidement.

## Placeholders à remplir

Le code contient des marqueurs `<!-- PLACEHOLDER: ... -->` dans `index.html`
pour chaque ressource manquante. Liste exhaustive :

### Polices `/assets/fonts/`

À télécharger depuis Google Fonts (Cormorant Garamond) et Adobe / Google
Fonts (Source Sans 3), convertir en `.woff2` puis déposer avec ces noms :

- `cormorant-garamond-regular.woff2`
- `cormorant-garamond-italic.woff2`
- `cormorant-garamond-medium.woff2`
- `source-sans-3-regular.woff2`
- `source-sans-3-medium.woff2`
- `source-sans-3-semibold.woff2`

> En attendant, le fallback Georgia / system fonctionne déjà — la page reste
> lisible et conserve son rythme typographique.

### Photos `/assets/photos/`

Format recommandé : `.webp` à 80 % + fallback `.jpg` à 85 %, max 1600 px de
large pour les principales, 800 px pour la galerie.

**Hero (chargement immédiat, prendre la plus forte)**
- `hero-jardin.webp` + `hero-jardin.jpg` — jardin de nuit recommandé
- `og-image.jpg` — version 1200×630 px pour partage WhatsApp / email

**Jardin (galerie section 5)**
- `jardin-jour-01.webp` à `jardin-jour-03.webp`
- `jardin-nuit-01.webp` à `jardin-nuit-02.webp`
- `jardin-detail-01.webp`

**Pièces (drawer du plan interactif — section 5 / plan-pieces)**
- `sejour-01.webp` à `sejour-03.webp`
- `cuisine-01.webp` à `cuisine-02.webp`
- `chambre-1-01.webp`
- `chambre-2-01.webp`
- `chambre-3-01.webp`
- `salle-eau-1-01.webp`
- `salle-eau-2-01.webp`
- `terrasse-01.webp`
- `entree-01.webp`
- `cellier-01.webp`
- `wc-01.webp`

Une fois les photos déposées, mettre à jour le tableau `ROOMS` dans le JS
en bas de `index.html` (chaque entrée a un champ `photos: []` à remplir).

**Parking (section 9)**
- `parking-cage-01.webp` + `parking-cage-02.webp`

### PDF `/assets/pdfs/`

- `dpe.pdf`
- `note_synthese.pdf`
- `amiante.pdf`
- `plomb.pdf`
- `termites.pdf`
- `electricite.pdf`
- `superficie_carrez.pdf`
- `accord_vis_a_vis.pdf` — celui-ci est embedé dans la section Jardin

> Une fois `accord_vis_a_vis.pdf` déposé, décommenter le bloc `<object>` dans
> la section Jardin de `index.html` et supprimer le `.pdf-placeholder`.

### Plan interactif `/assets/plan.svg`

Le plan SVG sera intégré **inline** dans `index.html`, à l'intérieur du
conteneur `#plan-host`. Chaque pièce (chaque `<path>` ou `<rect>`) doit avoir
un attribut `data-room` valant l'une de ces clés :

```
entree · chambre1 · chambre2 · chambre3 · sejour · cuisine ·
salle-eau-1 · salle-eau-2 · cellier · wc · terrasse · jardin
```

Le drawer s'ouvre automatiquement au clic sur tout élément `[data-room]`.
Aucun JS supplémentaire à écrire — la délégation d'événements est déjà en
place.

## Performance

- Toutes les images sont lazy-loaded (sauf le Hero).
- Le CSS et le JS sont inline pour éviter les requêtes supplémentaires.
- Cibles Lighthouse : Performance > 95, Accessibilité > 95, SEO > 90.

## SEO & confidentialité

- `<meta name="robots" content="noindex, nofollow">` est en place.
- `vercel.json` ajoute aussi le header `X-Robots-Tag: noindex, nofollow` sur
  toutes les routes.
- Aucun tracking, aucun cookie, aucune dépendance externe.
