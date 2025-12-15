# NU MVMT Shopify Theme

Custom Shopify theme based on Dawn 15.4.1 for NU MVMT Health and Athletics.

---

## Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher)
- [Shopify CLI](https://shopify.dev/docs/api/shopify-cli)
- Git
- A Shopify Partner account or store staff access

---

## 1. Install Shopify CLI

### macOS (Homebrew)
```bash
brew tap shopify/shopify
brew install shopify-cli
```

### Windows / npm
```bash
npm install -g @shopify/cli @shopify/theme
```

### Verify installation
```bash
shopify version
```

---

## 2. Authenticate with Shopify

```bash
shopify auth login
```

This opens a browser window. Log in with your Shopify Partner or store account.

---

## 3. Clone this Repository

```bash
git clone git@github.com:hdthaido/numvmt-shopify.git
cd numvmt-shopify
```

---

## 4. Connect to a Store

### Find your store URL
Your store URL is: `your-store-name.myshopify.com`

For NU MVMT: `numvmt-2.myshopify.com`

### Pull the current live theme (if needed)
```bash
shopify theme pull --store numvmt-2.myshopify.com
```

You'll be prompted to select which theme to pull from.

---

## 5. Start Development

> ⚠️ **Always pull before starting work** to ensure you have the latest changes:
> ```bash
> git pull origin main
> shopify theme pull --store numvmt-2.myshopify.com
> ```
> This syncs both the Git repo AND any changes made directly in the Shopify Theme Editor.

```bash
shopify theme dev --store numvmt-2.myshopify.com
```

This will:
- Sync your local files to a development theme on the store
- Start a local server at `http://127.0.0.1:9292`
- Watch for file changes and auto-sync

### Useful keyboard shortcuts (while dev server is running)
| Key | Action |
|-----|--------|
| `t` | Open theme preview in browser |
| `e` | Open Theme Editor (customizer) |
| `p` | Copy shareable preview link |
| `g` | Preview gift card |
| `q` | Quit |

---

## 6. Push Theme to Shopify

### Push to development theme
```bash
shopify theme push --store numvmt-2.myshopify.com
```

### Push to a specific theme (by ID)
```bash
shopify theme push --store numvmt-2.myshopify.com --theme <theme-id>
```

### Push and publish as live theme (⚠️ careful!)
```bash
shopify theme push --store numvmt-2.myshopify.com --live
```

---

## 7. Git Workflow

### Check status
```bash
git status
```

### Stage changes
```bash
git add .
```

### Commit with message
```bash
git commit -m "feat: your commit message"
```

### Push to GitHub
```bash
git push origin main
```

### If push is rejected (remote has changes)
```bash
git pull --rebase origin main
git push origin main
```

---

## Project Structure

```
numvmt/
├── assets/          # CSS, JS, images, SVGs
├── config/          # Theme settings (settings_schema.json, settings_data.json)
├── layout/          # Main layout files (theme.liquid, password.liquid)
├── locales/         # Translation files (51 languages)
├── sections/        # Page sections (modular, customizable)
├── snippets/        # Reusable Liquid partials
└── templates/       # Page templates (JSON format)
```

---

## Custom Sections

| Section | File | Description |
|---------|------|-------------|
| Hero Marquee | `sections/hero-marquee.liquid` | Homepage hero with dual-column vertical marquee |
| Booking Cards | `sections/booking-cards.liquid` | Clickable cards linking to external booking pages |

---

## Useful Commands

| Command | Description |
|---------|-------------|
| `shopify theme dev` | Start local development server |
| `shopify theme push` | Push theme to store |
| `shopify theme pull` | Pull theme from store |
| `shopify theme list` | List all themes on the store |
| `shopify theme info` | Show current theme info |
| `shopify theme check` | Run theme linting/validation |

---

## Troubleshooting

### "Theme cannot be previewed" error
Restart the dev server:
```bash
# Stop with Ctrl+C, then:
shopify theme dev --store numvmt-2.myshopify.com
```

### Liquid syntax error
Check the error message for the file and line number. Common issues:
- Can't use filters inside `if` conditions directly (use `assign` first)
- Missing `endif`, `endfor`, or `endcase`

### Changes not syncing
- Check terminal for sync errors
- Ensure you saved the file
- Restart dev server if needed

---

## Resources

- [Shopify Liquid Reference](https://shopify.dev/docs/api/liquid)
- [Dawn Theme Documentation](https://shopify.dev/docs/themes/dawn)
- [Shopify CLI Documentation](https://shopify.dev/docs/api/shopify-cli)
- [Theme Check (Linting)](https://shopify.dev/docs/themes/tools/theme-check)
