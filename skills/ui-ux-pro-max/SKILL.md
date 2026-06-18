---
name: ui-ux-pro-max
description: >-
  Skill d'expertise UI/UX pour auditer, concevoir et améliorer des interfaces
  web (HTML/CSS/JS). À utiliser quand l'utilisateur veut moderniser une
  interface, améliorer l'accessibilité, le responsive, la hiérarchie visuelle,
  les couleurs, la typographie, les micro-interactions, ou mettre en place un
  design system. Couvre l'audit heuristique, les tokens de design, le
  responsive mobile-first, l'accessibilité WCAG 2.2 AA et les patterns UI.
---

# UI/UX Pro Max

Skill pour transformer une interface fonctionnelle en interface **soignée,
accessible et cohérente**. Pensé pour des applications web en HTML/CSS/JS
(y compris fichier unique comme `index.html`).

## Quand l'utiliser

- « Modernise / améliore le design de cette page »
- « Rends ça plus pro / plus joli / plus lisible »
- « Audite l'UX de mon app »
- « Corrige l'accessibilité / le contraste / le responsive »
- « Mets en place un design system / des variables CSS »

## Méthode de travail (toujours dans cet ordre)

1. **Lire l'existant.** Identifier la structure HTML, le CSS en place
   (inline, `<style>`, classes), les couleurs/typo utilisées, le framework
   éventuel (Tailwind, Bootstrap, vanilla). Ne jamais réécrire à l'aveugle.
2. **Auditer** avec les heuristiques (`references/audit-checklist.md`).
   Lister 5 à 10 problèmes concrets, classés par impact.
3. **Proposer** une direction (palette, typo, espacement) AVANT de tout
   changer si la refonte est large. Pour des corrections ciblées, appliquer
   directement.
4. **Implémenter** par tokens d'abord (variables CSS), puis composants.
   Préserver le comportement JS existant et les `id`/sélecteurs utilisés
   par le code.
5. **Vérifier** : contraste, navigation clavier, responsive aux 3 points de
   rupture (mobile 375px, tablette 768px, desktop 1200px+).

## Principes directeurs

- **Mobile-first** : écrire le CSS de base pour mobile, puis `min-width`.
- **Tokens avant valeurs en dur** : couleurs, espacements, rayons, ombres et
  typo passent par des `--variables` CSS. Voir `references/design-tokens.md`.
- **Échelle d'espacement** cohérente (4/8px) : `4 8 12 16 24 32 48 64`.
- **Hiérarchie typographique** claire : 1 seule famille de titres, échelle
  modulaire (ex. ratio 1.25). Limiter à 2–3 graisses.
- **Contraste WCAG AA** : 4.5:1 texte normal, 3:1 texte large/icônes.
- **États visibles** : `:hover`, `:focus-visible`, `:active`, `:disabled`,
  loading, vide, erreur. Un composant n'est fini que quand ses états le sont.
- **Cohérence > originalité** : réutiliser les patterns existants de l'app.
- **Pas de régression fonctionnelle** : ne pas casser le JS, les formulaires,
  les `data-*`, les `id`.

## Fichiers de référence

- `references/design-tokens.md` — système de variables CSS prêt à coller
  (couleurs, typo, espacement, ombres, rayons, dark mode).
- `references/audit-checklist.md` — grille d'audit heuristique UX +
  accessibilité (WCAG 2.2 AA).
- `references/components.md` — patterns CSS pour boutons, formulaires, cartes,
  tableaux, modales, toasts, badges, navigation.
- `references/responsive.md` — stratégie mobile-first, breakpoints, grilles,
  tableaux responsives.

## Anti-patterns à corriger en priorité

- Texte gris clair sur fond blanc (contraste insuffisant).
- Cibles tactiles < 44×44px.
- Absence de `:focus-visible` (navigation clavier invisible).
- Tailles de police en `px` figées sans échelle / `<16px` sur mobile.
- Couleurs et marges en dur copiées partout (pas de tokens).
- Tableaux qui débordent sur mobile sans scroll ni adaptation.
- Boutons sans état de chargement sur actions asynchrones.
- Placeholder utilisé comme label (disparaît à la saisie).
- Pas de feedback après une action (sauvegarde, suppression).

## Livrable attendu

Après intervention, fournir un court résumé :
1. Problèmes corrigés (liste).
2. Décisions de design prises (palette/typo/espacement).
3. Points de vérification accessibilité/responsive faits.
4. Suggestions restantes éventuelles (par priorité).
