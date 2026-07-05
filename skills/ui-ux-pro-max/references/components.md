# Patterns de composants (CSS vanilla, basés sur les tokens)

Tous les composants utilisent les variables de `design-tokens.md`.
Toujours définir les états : hover, focus-visible, active, disabled.

## Base reset utile

```css
*, *::before, *::after { box-sizing: border-box; }
body {
  margin: 0;
  font-family: var(--font-sans);
  font-size: var(--text-base);
  line-height: var(--leading-normal);
  color: var(--color-text);
  background: var(--color-bg);
  -webkit-font-smoothing: antialiased;
}
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}
```

## Boutons

```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  min-height: var(--tap-target);
  padding: var(--space-2) var(--space-4);
  font-size: var(--text-sm);
  font-weight: var(--weight-semibold);
  border: 1px solid transparent;
  border-radius: var(--radius-md);
  cursor: pointer;
  transition: background var(--dur) var(--ease), transform var(--dur-fast) var(--ease);
}
.btn:active { transform: translateY(1px); }
.btn:disabled { opacity: 0.5; cursor: not-allowed; }

.btn-primary { background: var(--color-primary); color: var(--color-text-inverse); }
.btn-primary:hover:not(:disabled) { background: var(--color-primary-hover); }

.btn-secondary {
  background: var(--color-surface);
  color: var(--color-text);
  border-color: var(--color-border-strong);
}
.btn-secondary:hover:not(:disabled) { background: var(--color-surface-2); }

.btn-danger { background: var(--color-danger); color: #fff; }
.btn-ghost { background: transparent; color: var(--color-primary); }

/* État chargement : <button class="btn btn-primary" aria-busy="true"> */
.btn[aria-busy="true"] { pointer-events: none; opacity: 0.8; }
.btn[aria-busy="true"]::after {
  content: ""; width: 1em; height: 1em;
  border: 2px solid currentColor; border-right-color: transparent;
  border-radius: 50%; animation: spin 0.6s linear infinite;
}
@keyframes spin { to { transform: rotate(360deg); } }
```

## Champs de formulaire

```css
.field { display: flex; flex-direction: column; gap: var(--space-1); margin-bottom: var(--space-4); }
.field label { font-size: var(--text-sm); font-weight: var(--weight-medium); color: var(--color-text); }
.input, .select, .textarea {
  min-height: var(--tap-target);
  padding: var(--space-2) var(--space-3);
  font-size: var(--text-base);   /* 16px : pas de zoom iOS */
  color: var(--color-text);
  background: var(--color-bg);
  border: 1px solid var(--color-border-strong);
  border-radius: var(--radius-md);
  transition: border-color var(--dur) var(--ease), box-shadow var(--dur) var(--ease);
}
.input:focus, .select:focus, .textarea:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px var(--color-primary-soft);
}
.input[aria-invalid="true"] { border-color: var(--color-danger); }
.field .error { font-size: var(--text-xs); color: var(--color-danger); }
.field .hint { font-size: var(--text-xs); color: var(--color-text-subtle); }
```

## Cartes

```css
.card {
  background: var(--color-bg);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
  padding: var(--space-5);
}
.card--interactive { transition: box-shadow var(--dur) var(--ease), transform var(--dur) var(--ease); cursor: pointer; }
.card--interactive:hover { box-shadow: var(--shadow-md); transform: translateY(-2px); }
```

## Badges / statuts (jamais la couleur seule)

```css
.badge {
  display: inline-flex; align-items: center; gap: var(--space-1);
  padding: 2px var(--space-2);
  font-size: var(--text-xs); font-weight: var(--weight-semibold);
  border-radius: var(--radius-full);
}
.badge--success { background: #dcfce7; color: #166534; }
.badge--warning { background: #fef3c7; color: #92400e; }
.badge--danger  { background: #fee2e2; color: #991b1b; }
.badge--info    { background: var(--color-primary-soft); color: var(--color-primary-active); }
/* Ajouter un point ou une icône en plus de la couleur pour l'accessibilité */
```

## Tableaux

```css
.table-wrap { overflow-x: auto; -webkit-overflow-scrolling: touch; border-radius: var(--radius-md); }
.table { width: 100%; border-collapse: collapse; font-size: var(--text-sm); }
.table th {
  text-align: left; padding: var(--space-3);
  font-weight: var(--weight-semibold); color: var(--color-text-muted);
  background: var(--color-surface); border-bottom: 1px solid var(--color-border);
  position: sticky; top: 0;
}
.table td { padding: var(--space-3); border-bottom: 1px solid var(--color-border); }
.table tr:hover td { background: var(--color-surface); }
```

## Modale

```css
.modal-backdrop {
  position: fixed; inset: 0; background: rgba(15,23,42,0.5);
  display: grid; place-items: center; padding: var(--space-4); z-index: 50;
}
.modal {
  background: var(--color-bg); border-radius: var(--radius-lg);
  box-shadow: var(--shadow-lg); width: min(560px, 100%);
  max-height: 90vh; overflow-y: auto; padding: var(--space-6);
}
```
Comportement : fermeture par Échap et clic sur le backdrop, focus piégé dans
la modale, focus rendu à l'élément déclencheur à la fermeture, `role="dialog"`
+ `aria-modal="true"` + `aria-labelledby`.

## Toast / notification

```css
.toast-region { position: fixed; bottom: var(--space-4); right: var(--space-4); display: flex; flex-direction: column; gap: var(--space-2); z-index: 60; }
.toast {
  display: flex; align-items: center; gap: var(--space-3);
  padding: var(--space-3) var(--space-4);
  background: var(--color-text); color: var(--color-text-inverse);
  border-radius: var(--radius-md); box-shadow: var(--shadow-lg);
}
```
Le conteneur doit avoir `aria-live="polite"` (ou `assertive` pour les
erreurs) pour être annoncé aux lecteurs d'écran.

## États vides

Toujours prévoir : icône/illustration légère + titre + 1 phrase + action
principale. Ne jamais laisser une zone vide sans explication.
