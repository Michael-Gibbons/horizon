# Copilot Instructions for Horizon Theme

This is a **Shopify Horizon theme** codebase. Follow these standards and patterns when generating or modifying code.

## Project Structure

- `assets/` - CSS and JavaScript files
- `blocks/` - Reusable block components (liquid)
- `config/` - Theme settings (`settings_schema.json`, `settings_data.json`)
- `layout/` - Theme layouts
- `locales/` - Translation files
- `sections/` - Theme sections (liquid)
- `snippets/` - Reusable snippets (liquid)
- `templates/` - Page templates
- `tokens.json` - Design tokens (Figma Tokens Studio format)

## Coding Standards

Detailed rules are in `.cursor/rules/`. Key standards:

### CSS Standards (`.cursor/rules/css-standards.mdc`)

- **Never** use IDs as selectors
- **Never** hardcode colors — always use CSS variables from color schemes
- Keep specificity at `0 1 0` (single class) when possible
- Maximum specificity: `0 4 0`
- Avoid `!important` — if necessary, add a comment explaining why
- Global variables go in `snippets/theme-styles-variables.liquid`
- Scope component variables to their class
- Use `:has()` sparingly due to performance — prefer server-rendered classes

### Liquid Standards (`.cursor/rules/liquid.mdc`)

- ⚠️ **NEVER edit `{% schema %}` blocks directly** — schemas are generated from `schemas/` folder
- Use `{% liquid %}` tags for multiline Liquid code
- Use `{% # comment %}` for inline comments
- Never invent new filters, tags, or objects

### JavaScript Standards (`.cursor/rules/javascript-standards.mdc`)

- Use Web Components (custom elements) for interactive components
- Prefer vanilla JS over frameworks
- Use ES modules

### HTML Standards (`.cursor/rules/html-standards.mdc`)

- Semantic HTML elements
- Proper heading hierarchy
- ARIA attributes where needed

## Accessibility

Follow WCAG 2.1 AA standards. Key rules in `.cursor/rules/`:

- `global-accessibility-standards.mdc` - Core accessibility requirements
- `focus-order-and-styles-accessibility.mdc` - Focus management
- `form-accessibility.mdc` - Form labeling and errors
- `modal-accessibility.mdc` - Dialog/modal patterns
- `color-contrast-accessibility.mdc` - Color contrast ratios

### Critical Accessibility Patterns

- All interactive elements must be keyboard accessible
- Minimum touch target: 44x44px
- Color contrast: 4.5:1 for text, 3:1 for large text
- Always provide text alternatives for images
- Use `aria-live` regions for dynamic content updates

## Design Tokens

Reference `tokens.json` for consistent values:

- **Colors**: Use color scheme variables (`--color-background`, `--color-foreground`, `--color-primary`, etc.)
- **Spacing**: Use spacing tokens (`--spacing-xs` through `--spacing-6xl`)
- **Typography**: Use font variables (`--font-body--family`, `--font-heading--family`)
- **Border radius**: Use radius tokens (`--style-border-radius-sm`, `--style-border-radius-md`)

## Color Schemes

The theme supports multiple color schemes. Always use CSS variables:

```css
/* ✅ Correct */
color: var(--color-foreground);
background: var(--color-background);

/* ❌ Wrong */
color: #000000;
background: white;
```

## Component Patterns

### Buttons

- Primary: `.button--primary`
- Secondary: `.button--secondary`
- Use `--style-border-radius-buttons-primary` / `--style-border-radius-buttons-secondary`

### Inputs

- Use `--style-border-radius-inputs`
- Use `--color-input-*` variables for colors

### Cards

- Product cards: `snippets/product-card.liquid`
- Collection cards: `snippets/collection-card.liquid`
- Resource cards: `snippets/resource-card.liquid`

## Localization

- All user-facing strings must use translation keys
- Format: `{{ 'key.path' | t }}`
- Translations in `locales/` folder

## Before Making Changes

1. Check if a similar pattern exists in the codebase
2. Reference the appropriate `.cursor/rules/*.mdc` file for detailed standards
3. Ensure accessibility compliance
4. Use design tokens from `tokens.json` or CSS variables


## Design Standards

- Follow the design tokens defined in `tokens.json` and the rules found in `.cursor/rules/design-tokens.mdc`
- Maintain consistent spacing, typography, and color usage
- Ensure components adhere to the theme's color schemes