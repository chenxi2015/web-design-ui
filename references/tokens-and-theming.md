# Tokens & Theming

## Full token table

| Variable | Light value | Dark value | Notes |
|---|---|---|---|
| `--background` | `0 0% 100%` | `0 0% 4%` | Page canvas |
| `--foreground` | `222 47% 11%` | `210 40% 97%` | Body text |
| `--card` | `0 0% 99%` | `220 13% 7%` | Card surface |
| `--primary` | `222 47% 11%` | `210 40% 97%` | Main accent (black by default) |
| `--primary-foreground` | `0 0% 100%` | `0 0% 4%` | Text on primary |
| `--secondary` | `210 20% 96%` | `220 13% 11%` | Subtle fills |
| `--muted-foreground` | `215 16% 52%` | `215 10% 33%` | Placeholder, captions |
| `--border` | `214 20% 90%` | `220 13% 13%` | Default borders |
| `--ring` | same as `--primary` | same as `--primary` | Focus ring |

## Theme toggle hook

```jsx
import { useState } from "react"
import { Switch } from "@/components/ui/switch"

export default function App() {
  const [dark,  setDark]  = useState(false)
  const [green, setGreen] = useState(false)

  return (
    <div className={`${dark ? "mint-dark" : "mint-light"} ${green ? "mint-accent-green" : ""} min-h-screen bg-background text-foreground transition-colors duration-300`}>

      {/* Toggle in nav */}
      <div className="flex items-center gap-2">
        <span className="text-xs text-muted-foreground">{dark ? "🌙" : "☀️"}</span>
        <Switch checked={dark} onCheckedChange={setDark} className="scale-75" />
      </div>
    </div>
  )
}
```

## Dynamic --primary via inline style

Use this to switch brand color at runtime (e.g. color picker demo):

```jsx
const PALETTES = [
  { name: "Midnight", light: "222 47% 11%", dark: "210 40% 97%", swatch: "#1e3a8a" },
  { name: "Emerald",  light: "158 79% 36%", dark: "158 79% 43%", swatch: "#10b981" },
  { name: "Violet",   light: "258 90% 56%", dark: "258 90% 66%", swatch: "#8b5cf6" },
  { name: "Sky",      light: "199 89% 42%", dark: "199 89% 55%", swatch: "#0ea5e9" },
  { name: "Rose",     light: "346 77% 50%", dark: "346 77% 62%", swatch: "#f43f5e" },
  { name: "Amber",    light: "32 95% 44%",  dark: "38 92% 55%",  swatch: "#f59e0b" },
  { name: "Teal",     light: "173 80% 34%", dark: "173 80% 44%", swatch: "#14b8a6" },
  { name: "Pink",     light: "322 84% 48%", dark: "322 84% 62%", swatch: "#ec4899" },
]

const pal     = PALETTES[idx]
const primary = dark ? pal.dark : pal.light
const prFg    = dark ? (idx === 0 ? "0 0% 4%" : "0 0% 100%") : "0 0% 100%"

<div style={{ "--primary": primary, "--primary-foreground": prFg, "--ring": primary }}>
```

All gradient colors, badge tints, icon boxes, active tabs, stat numbers, and glow use `hsl(var(--primary) / opacity)` and update automatically.
