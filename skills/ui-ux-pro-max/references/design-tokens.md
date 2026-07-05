# Design Tokens — variables CSS prêtes à l'emploi

Coller dans un `:root`. Adapter les valeurs de marque, garder la structure.
Toujours référencer les tokens (`var(--…)`) dans le reste du CSS plutôt que
des valeurs en dur.

```css
:root {
  /* ----- Couleurs de marque ----- */
  --color-primary: #2563eb;       /* bleu action */
  --color-primary-hover: #1d4ed8;
  --color-primary-active: #1e40af;
  --color-primary-soft: #eff6ff;  /* fond léger */

  --color-accent: #7c3aed;
  --color-success: #16a34a;
  --color-warning: #d97706;
  --color-danger: #dc2626;
  --color-info: #0891b2;

  /* ----- Neutres (gris) ----- */
  --color-bg: #ffffff;
  --color-surface: #f8fafc;       /* cartes, panneaux */
  --color-surface-2: #f1f5f9;
  --color-border: #e2e8f0;
  --color-border-strong: #cbd5e1;

  --color-text: #0f172a;          /* texte principal */
  --color-text-muted: #475569;    /* texte secondaire (contraste OK) */
  --color-text-subtle: #64748b;   /* labels, légendes */
  --color-text-inverse: #ffffff;

  /* ----- Typographie ----- */
  --font-sans: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  --font-mono: "JetBrains Mono", ui-monospace, SFMono-Regular, monospace;

  --text-xs: 0.75rem;    /* 12 */
  --text-sm: 0.875rem;   /* 14 */
  --text-base: 1rem;     /* 16 — jamais moins sur mobile */
  --text-lg: 1.125rem;   /* 18 */
  --text-xl: 1.25rem;    /* 20 */
  --text-2xl: 1.5rem;    /* 24 */
  --text-3xl: 1.875rem;  /* 30 */
  --text-4xl: 2.25rem;   /* 36 */

  --leading-tight: 1.2;
  --leading-normal: 1.5;
  --leading-relaxed: 1.65;

  --weight-normal: 400;
  --weight-medium: 500;
  --weight-semibold: 600;
  --weight-bold: 700;

  /* ----- Espacement (échelle 4/8) ----- */
  --space-1: 0.25rem;  /* 4  */
  --space-2: 0.5rem;   /* 8  */
  --space-3: 0.75rem;  /* 12 */
  --space-4: 1rem;     /* 16 */
  --space-5: 1.5rem;   /* 24 */
  --space-6: 2rem;     /* 32 */
  --space-7: 3rem;     /* 48 */
  --space-8: 4rem;     /* 64 */

  /* ----- Rayons ----- */
  --radius-sm: 6px;
  --radius-md: 10px;
  --radius-lg: 16px;
  --radius-full: 9999px;

  /* ----- Ombres ----- */
  --shadow-sm: 0 1px 2px rgba(15, 23, 42, 0.06);
  --shadow-md: 0 4px 12px rgba(15, 23, 42, 0.08);
  --shadow-lg: 0 12px 32px rgba(15, 23, 42, 0.12);

  /* ----- Transitions ----- */
  --ease: cubic-bezier(0.4, 0, 0.2, 1);
  --dur-fast: 120ms;
  --dur: 200ms;

  /* ----- Layout ----- */
  --container-max: 1200px;
  --tap-target: 44px;  /* taille mini cible tactile */
}

/* ----- Dark mode (optionnel) ----- */
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg: #0f172a;
    --color-surface: #1e293b;
    --color-surface-2: #334155;
    --color-border: #334155;
    --color-border-strong: #475569;
    --color-text: #f1f5f9;
    --color-text-muted: #cbd5e1;
    --color-text-subtle: #94a3b8;
    --color-primary-soft: #1e3a5f;
    --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.3);
    --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.4);
    --shadow-lg: 0 12px 32px rgba(0, 0, 0, 0.5);
  }
}

/* Respect des préférences de mouvement */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## Règles d'usage

- **Couleurs** : ne jamais écrire `#fff`/`#333` dans les composants → token.
- **Texte secondaire** : utiliser `--color-text-muted` (≥4.5:1), pas un gris
  arbitraire trop clair.
- **Espacement** : composer avec l'échelle, éviter `13px`, `7px`, etc.
- **Police mobile** : corps de texte ≥ `--text-base` (16px) pour éviter le
  zoom automatique iOS sur les champs.
