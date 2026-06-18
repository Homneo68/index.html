# Stratégie responsive (mobile-first)

## Méta viewport (obligatoire dans `<head>`)

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

## Breakpoints

Écrire le CSS de base pour mobile, puis enrichir avec `min-width`.

```css
/* Base = mobile (< 640px) */

@media (min-width: 640px)  { /* sm — grande mobile / petite tablette */ }
@media (min-width: 768px)  { /* md — tablette */ }
@media (min-width: 1024px) { /* lg — desktop */ }
@media (min-width: 1280px) { /* xl — large desktop */ }
```

## Conteneur fluide

```css
.container {
  width: 100%;
  max-width: var(--container-max);
  margin-inline: auto;
  padding-inline: var(--space-4);
}
@media (min-width: 768px) { .container { padding-inline: var(--space-6); } }
```

## Grilles modernes

```css
/* Grille auto-responsive sans media query */
.grid-auto {
  display: grid;
  gap: var(--space-4);
  grid-template-columns: repeat(auto-fill, minmax(min(260px, 100%), 1fr));
}

/* Sidebar + contenu qui s'empile sur mobile */
.layout {
  display: grid;
  gap: var(--space-5);
  grid-template-columns: 1fr;
}
@media (min-width: 1024px) {
  .layout { grid-template-columns: 260px 1fr; }
}
```

## Tableaux responsives

**Option A — scroll horizontal** (simple, garde la structure) :
```html
<div class="table-wrap"><table class="table">…</table></div>
```

**Option B — cartes empilées sur mobile** (meilleure lecture) :
```css
@media (max-width: 767px) {
  .table-cards thead { display: none; }
  .table-cards tr {
    display: block; margin-bottom: var(--space-3);
    border: 1px solid var(--color-border); border-radius: var(--radius-md);
    padding: var(--space-3);
  }
  .table-cards td {
    display: flex; justify-content: space-between; gap: var(--space-3);
    padding: var(--space-1) 0; border: none;
  }
  .table-cards td::before {
    content: attr(data-label);
    font-weight: var(--weight-semibold); color: var(--color-text-muted);
  }
}
```
(Chaque `<td data-label="Nom de colonne">` pour afficher l'entête en mobile.)

## Navigation

- Mobile : menu burger ou barre d'onglets en bas (`position: sticky; bottom: 0`).
- Desktop : barre horizontale ou sidebar.
- Toujours marquer la page active (`aria-current="page"`).

## Bonnes pratiques

- Unités relatives (`rem`, `%`, `fr`, `clamp()`) plutôt que `px` figés.
- `clamp()` pour la typo fluide : `font-size: clamp(1.5rem, 4vw, 2.25rem);`
- Images : `max-width: 100%; height: auto;`.
- Tester à 320–375px (petit mobile), 768px (tablette), 1280px+ (desktop).
- Zones tactiles ≥ 44px, espacées d'au moins 8px.
- Éviter le `hover` comme seul moyen d'accès (pas de hover au tactile).
```
