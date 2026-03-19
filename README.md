# web-design-ui

A reusable `skills` package for building UI in the Mintlify design style using shadcn/ui.

## What this skill does

- Generates React + shadcn/ui interfaces with Mintlify's aesthetic
- Dual dark/light mode with smooth CSS variable switching
- Default: shadcn neutral black — opt-in Mintlify green accent
- Hero gradient presets (mesh, radial, grid, aurora) — all via `hsl(var(--primary))`
- Lucide icon integration (static + 7 CSS animation patterns)
- Framework-agnostic CSS token layer (works in Vue, Svelte, Solid, vanilla HTML)

## File structure

```text
web-design-ui/
├── SKILL.md                         ← Main skill entry
└── references/
    ├── tokens-and-theming.md        ← Full token table, 8 palette presets
    ├── components.md                ← Button, Card, Badge, Nav, Tabs patterns
    ├── hero-gradients.md            ← 4 hero presets with full CSS
    ├── icons.md                     ← lucide-react + 7 animation classes
    └── framework-agnostic.md        ← Vue / Svelte / Solid / HTML examples
```

## Installation

Install this skill with the generic `skills` CLI workflow.

### Recommended — Install from GitHub

```bash
npx skills add https://github.com/chenxi2015/web-design-ui --skill web-design-ui
```

### Local repository install

If you already cloned this repository locally, install from the current folder:

```bash
npx skills add . --skill web-design-ui
```

### Manual install

If your environment uses a local skills directory, copy the full project folder so `SKILL.md` and `references/` stay together:

```bash
mkdir -p .skills/web-design-ui
cp SKILL.md .skills/web-design-ui/
cp -R references .skills/web-design-ui/
```

### Notes

Use `npx skills add <source> --skill web-design-ui` as the standard install pattern.

`<source>` can be:

- a GitHub repository URL
- a local directory
- another supported remote source that contains this skill

## Usage

After installation, invoke `web-design-ui` with prompts like:

- *"Build a Mintlify-style landing page"*
- *"Create a dark SaaS dashboard with shadcn"*
- *"参考 Mintlify 风格生成一个产品页"*
- *"Add light/dark mode toggle to this component"*
- *"Use the Mintlify green accent"*

## Design tokens

All colors use `hsl(var(--primary) / opacity)`:

```css
.mint-light { --primary: 222 47% 11%; }  /* black — default */
.mint-dark  { --primary: 210 40% 97%; }  /* near-white */

/* Opt-in green */
.mint-accent-green.mint-light { --primary: 158 79% 36%; }
.mint-accent-green.mint-dark  { --primary: 158 79% 43%; }
```

## License

MIT
