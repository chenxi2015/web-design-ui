# mintlify-style

A Claude skill for building UI in the Mintlify design style using shadcn/ui.

## What this skill does

- Generates React + shadcn/ui interfaces with Mintlify's aesthetic
- Dual dark/light mode with smooth CSS variable switching
- Default: shadcn neutral black — opt-in Mintlify green accent
- Hero gradient presets (mesh, radial, grid, aurora) — all via `hsl(var(--primary))`
- Lucide icon integration (static + 7 CSS animation patterns)
- Framework-agnostic CSS token layer (works in Vue, Svelte, Solid, vanilla HTML)

## File structure

```
mintlify-style/
├── SKILL.md                          ← Main skill file (loaded by Claude)
└── references/
    ├── tokens-and-theming.md         ← Full token table, 8 palette presets
    ├── components.md                 ← Button, Card, Badge, Nav, Tabs patterns
    ├── hero-gradients.md             ← 4 hero presets with full CSS
    ├── icons.md                      ← lucide-react + 7 animation classes
    └── framework-agnostic.md        ← Vue / Svelte / Solid / HTML examples
```

## Installation

### Option 1 — Claude.ai Skills UI
Upload `SKILL.md` (and optionally the `references/` folder) via **Settings → Skills**.

### Option 2 — npx (if supported by your Claude CLI)
```bash
npx skills install mintlify-style
```

### Option 3 — Manual copy
Copy the entire `mintlify-style/` folder into your project's `.skills/` directory, or wherever your Claude skills are configured.

## Usage

Once installed, trigger the skill by asking Claude:

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
