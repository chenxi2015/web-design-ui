---
name: web-design-ui
description: Build React UI components, pages, and apps in the Mintlify design style using shadcn/ui as the component foundation. Supports both dark mode and light mode with a theme toggle. Use this skill whenever the user asks for a "Mintlify-style" interface, dark or light SaaS UI, docs-style design, developer tool aesthetic — especially when shadcn/ui components are involved. Also trigger for "参考 Mintlify 风格", "Mintlify 样式", "白天模式", "日间模式", "深色/浅色切换". Default color scheme is shadcn/ui's neutral black — green accent is opt-in only when user explicitly requests Mintlify green branding.
---

# web-design-ui

**Core principle:** shadcn/ui components as-is. CSS variable overrides for theme. Default = shadcn neutral black. Green = opt-in only.

---

## Quick Reference

### Root setup

```jsx
// Wrap root with mode class + inject CSS variables via style prop
<div
  className={`${dark ? "mint-dark" : "mint-light"} ${green ? "mint-accent-green" : ""} min-h-screen bg-background text-foreground transition-colors duration-300`}
  style={{ "--primary": primary, "--primary-foreground": prFg, "--ring": primary }}
>
```

### CSS token blocks (inject in globals.css or `<style>` tag)

```css
/* Light — shadcn neutral black */
.mint-light {
  --background: 0 0% 100%;   --foreground: 222 47% 11%;
  --card: 0 0% 99%;          --card-foreground: 222 47% 11%;
  --primary: 222 47% 11%;    --primary-foreground: 0 0% 100%;
  --secondary: 210 20% 96%;  --secondary-foreground: 215 16% 40%;
  --muted: 210 20% 96%;      --muted-foreground: 215 16% 52%;
  --border: 214 20% 90%;     --input: 214 20% 90%;
  --ring: 222 47% 11%;       --radius: 0.625rem;
}
/* Dark — shadcn neutral */
.mint-dark {
  --background: 0 0% 4%;    --foreground: 210 40% 97%;
  --card: 220 13% 7%;       --card-foreground: 210 40% 97%;
  --primary: 210 40% 97%;   --primary-foreground: 0 0% 4%;
  --secondary: 220 13% 11%; --secondary-foreground: 215 16% 62%;
  --muted: 220 13% 11%;     --muted-foreground: 215 10% 33%;
  --border: 220 13% 13%;    --input: 220 13% 13%;
  --ring: 210 40% 97%;      --radius: 0.625rem;
}
/* Opt-in green accent */
.mint-accent-green.mint-light { --primary: 158 79% 36%; --primary-foreground: 0 0% 100%; --ring: 158 79% 36%; }
.mint-accent-green.mint-dark  { --primary: 158 79% 43%; --primary-foreground: 0 0% 100%; --ring: 158 79% 43%; }
```

---

## Key Rules

### Cards — zero shadow, border only
```jsx
<Card className="shadow-none border-slate-200/70 dark:border-border/70
  transition-colors duration-150
  hover:border-foreground/15 hover:bg-foreground/[0.02]">
```
**Never add `hover:shadow-*` to cards or buttons.**

### Icon box — dark mode safe
```css
/* Light: colorful tint. Dark: neutral tint (readable regardless of --primary) */
.mint-light .icon-box { background: hsl(var(--primary) / .1); }
.mint-dark  .icon-box { background: hsl(var(--foreground) / .07); border: 1px solid hsl(var(--foreground) / .06); }
.icon-box .lucide     { color: hsl(var(--primary)); }
```

### Primary button — always white text
```jsx
// Green gradient CTA (only when green accent active)
<Button className="border-0 font-semibold text-white"
  style={{ background: "linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary) / .8))" }}>
// Default — use shadcn Button as-is, inherits --primary token
<Button>Get started</Button>
```

### Gradient headline
```jsx
<h1>
  <span className="bg-gradient-to-b from-foreground to-foreground/50 bg-clip-text text-transparent">The Intelligent</span>
  {" "}<span style={{ color: "hsl(var(--primary))" }}>Knowledge Platform</span>
</h1>
```

---

## Reference Files

Read these when you need full detail on a specific topic:

| File | When to read |
|---|---|
| `references/tokens-and-theming.md` | Full token table, theme toggle hook, 8 palette presets |
| `references/components.md` | Button, Card, Badge, Input, Nav, Tabs, Dialog patterns |
| `references/hero-gradients.md` | 4 hero gradient presets (mesh, radial, grid, aurora) + CSS |
| `references/icons.md` | lucide-react static icons + 7 CSS animation patterns |
| `references/framework-agnostic.md` | Vue / Svelte / Solid / HTML usage, lucide per-framework |

---

## Checklist Before Output

- [ ] Both `mint-light` AND `mint-dark` token blocks present
- [ ] Root element gets `mint-dark` or `mint-light` class dynamically
- [ ] Theme toggle in nav (`Switch` or button swapping class)
- [ ] `transition-colors duration-300` on root wrapper
- [ ] Cards: `shadow-none` + `hover:border-foreground/15` — **no shadow**
- [ ] Icon boxes: separate light/dark CSS rules (not just `hsl(var(--primary)/.1)`)
- [ ] Primary buttons: white text (`text-white` or `text-primary-foreground`)
- [ ] Gradient headline uses `from-foreground to-foreground/50`
- [ ] All gradient colors use `hsl(var(--primary) / opacity)` — no hardcoded hex
- [ ] Hero section uses one of the 4 presets from `references/hero-gradients.md`
- [ ] Lucide icons: single-line import `import { X, Y } from "lucide-react"`
