# GAP Foods

Single-page marketing site for **GAP Foods**, a wholesale bakery manufacturer in Coimbatore supplying cafés, canteens, caterers and event partners across Tamil Nadu.

Live site: [gapfoods.in](https://gapfoods.in)

## Stack

Static HTML with no build step or dependencies. One `index.html` holds the markup and an inline `<style>` block; fonts load from Google Fonts.

- **Display type** — Sora
- **Body type** — Inter
- **Images** — WebP, lazy-loaded with explicit dimensions to avoid layout shift

## Running locally

Any static file server works. With Python:

```bash
python -m http.server 8642
```

Then open <http://localhost:8642>.

## Structure

```
index.html              markup + inline styles
assets/
  logo.png              GAP Foods logo (transparent)
  nutrilae-logo.png     Nutrilae sub-brand logo (transparent)
  products/             product and lifestyle photography (WebP)
.claude/launch.json     dev-server config
```

## Sections

Hero · Who We Bake For · Product highlights · Why GAP Foods · Our Story · Our Range · Nutrilae (sub-brand) · Customers · Contact

## Content policy

The site is built from an internal wholesale product list (`GAP FOODS.pdf`), which is **git-ignored and must not be committed**. That document contains wholesale prices, MRP and per-product profit margins.

Only non-commercial detail belongs on the public site: product names, categories, ingredients, shelf life and storage guidance. **No pricing, margin or other business information.**

## Design tokens

Defined as CSS custom properties on `:root` in `index.html`:

| Token | Value | Use |
| --- | --- | --- |
| `--green-900` | `#0f5c33` | headings, primary hover |
| `--green-700` | `#158a47` | primary buttons, icons |
| `--gold-500` | `#d4a017` | accent, sub-brand |
| `--cream` | `#fffaf0` | page background |
| `--ink` / `--ink-soft` | `#20261f` / `#4c564a` | body text |

Buttons are driven by three per-variant properties (`--btn-bg`, `--btn-fg`, `--btn-bd`); the base `.btn` rule owns all geometry and motion, so variants stay dimensionally identical.

## Accessibility notes

- Gold buttons use dark ink (`#3a2a05`), not white — white on `--gold-500` measures ~2.3:1 and fails WCAG AA
- Icon-only links (social) carry `aria-label`s
- All interactive targets are at least 44px
- `prefers-reduced-motion` disables scroll reveals and transitions
