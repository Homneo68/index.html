# Grille d'audit UX + Accessibilité

Parcourir dans l'ordre. Noter chaque problème avec : élément concerné,
sévérité (bloquant / majeur / mineur), correction proposée.

## 1. Heuristiques d'utilisabilité (Nielsen)

- [ ] **Visibilité de l'état** : l'utilisateur sait toujours où il est et ce
      qui se passe (chargement, succès, erreur).
- [ ] **Correspondance au réel** : libellés clairs, vocabulaire métier, pas de
      jargon technique inutile.
- [ ] **Contrôle & liberté** : annuler, revenir en arrière, fermer une modale
      (Échap), confirmer les actions destructrices.
- [ ] **Cohérence & standards** : mêmes patterns pour mêmes actions partout.
- [ ] **Prévention des erreurs** : validation en amont, confirmations,
      désactivation des actions impossibles.
- [ ] **Reconnaissance > rappel** : options visibles, pas à mémoriser.
- [ ] **Flexibilité** : raccourcis, valeurs par défaut intelligentes.
- [ ] **Design épuré** : pas de surcharge, hiérarchie claire.
- [ ] **Gestion des erreurs** : messages explicites, en langage humain,
      avec la solution.
- [ ] **Aide & documentation** : tooltips, placeholders d'exemple, états vides
      explicatifs.

## 2. Hiérarchie visuelle

- [ ] Un seul point focal par écran/section.
- [ ] Échelle typographique cohérente (titres > sous-titres > corps).
- [ ] Espacement qui groupe les éléments liés (proximité).
- [ ] Alignement régulier (grille).
- [ ] Couleur d'accent réservée aux actions principales (1 CTA primaire/vue).

## 3. Accessibilité (WCAG 2.2 AA)

- [ ] **Contraste** : 4.5:1 texte normal, 3:1 texte large (≥24px ou ≥19px
      gras) et composants UI/icônes.
- [ ] **Clavier** : tout est atteignable et utilisable au clavier ; ordre de
      tabulation logique ; pas de piège au focus.
- [ ] **Focus visible** : `:focus-visible` net sur chaque élément interactif.
- [ ] **Cibles tactiles** : ≥ 44×44px (WCAG 2.2 : 24px minimum).
- [ ] **Labels** : chaque champ a un `<label>` associé (`for`/`id`), pas
      seulement un placeholder.
- [ ] **Alternatives textuelles** : `alt` sur images informatives, `alt=""`
      sur décoratives.
- [ ] **Structure** : un seul `<h1>`, hiérarchie de titres sans saut, balises
      sémantiques (`<nav> <main> <button> <table>`...).
- [ ] **ARIA** : `aria-label`, `aria-live` (toasts/erreurs), `role` quand le
      HTML natif ne suffit pas — mais natif d'abord.
- [ ] **Couleur seule** : l'information n'est jamais portée par la couleur
      uniquement (ajouter icône/texte).
- [ ] **Zoom** : utilisable à 200% sans perte de contenu.
- [ ] **Mouvement** : respecter `prefers-reduced-motion`.

## 4. Formulaires

- [ ] Labels visibles et persistants.
- [ ] Types d'input adaptés (`email`, `tel`, `number`, `date`).
- [ ] Messages d'erreur sous le champ, liés via `aria-describedby`.
- [ ] Validation au bon moment (à la soumission ou au blur, pas à chaque
      frappe pour les erreurs dures).
- [ ] Bouton de soumission avec état loading + désactivation anti double-clic.
- [ ] Autocomplete (`autocomplete="..."`) sur les champs courants.

## 5. Responsive

- [ ] Pas de scroll horizontal involontaire.
- [ ] Lisible et utilisable à 375px de large.
- [ ] Tableaux : scroll horizontal encapsulé OU transformation en cartes.
- [ ] Menus/navigation adaptés (burger, bottom bar).
- [ ] Images fluides (`max-width:100%`).

## 6. Performance perçue

- [ ] Skeletons/spinners pour les chargements > 300ms.
- [ ] Feedback immédiat au clic (état actif).
- [ ] Pas de layout shift au chargement.

## Format de restitution

```
🔴 Bloquant
- [Champ login] Contraste 2.1:1 sur le texte d'aide → passer à --color-text-muted (4.8:1)

🟠 Majeur
- [Tableau offres] Déborde à 375px → wrapper overflow-x:auto + min-width

🟡 Mineur
- [Boutons] Pas de :focus-visible → ajouter outline 2px
```
