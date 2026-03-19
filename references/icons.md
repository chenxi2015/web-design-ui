# Icon System

## Static icons — lucide-react

Browse at [lucide.dev](https://lucide.dev). Available as `lucide-react` in React projects.

**Critical: always single-line import in artifacts**

```jsx
// ✅ Single line — artifact scanner can parse this
import { Zap, Bot, RefreshCw, Lock, Globe, BarChart2 } from "lucide-react"

// ❌ Multi-line — artifact scanner fails with "{ } from lucide-react"
import {
  Zap, Bot,
} from "lucide-react"
```

Basic usage:
```jsx
<Zap size={16} className="lucide" strokeWidth={1.75} />

// Inside icon box
<div className="icon-box ia-float">
  <Zap size={16} className="lucide" strokeWidth={1.75} />
</div>
```

## Icon sizing

| Context | Size | Class |
|---|---|---|
| Inline / button | 12–14px | `size={12}` |
| Feature card icon box | 16px | `size={16}` |
| Animation catalog | 18px | `size={18}` |
| Decorative / CTA | 22–24px | `size={22}` |

## Animated icons — lucide-animated.com style

Browse originals at [lucide-animated.com](https://lucide-animated.com).  
The site is copy-paste SVG — no npm package. In React projects: use `lucide-react` + these CSS animations.

```css
/* 1. Spin on hover — RefreshCw, Settings, Loader */
@keyframes ia-spin { to { transform: rotate(360deg); } }
.ia-spin-hover:hover .lucide { animation: ia-spin .55s ease; }

/* 2. Float loop — Cloud, Rocket, Upload */
@keyframes ia-float { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-3px)} }
.ia-float .lucide { animation: ia-float 2.6s ease-in-out infinite; }

/* 3. Shake on hover — Bell, AlertTriangle */
@keyframes ia-shake { 0%,100%{transform:rotate(0)} 20%{transform:rotate(-12deg)} 60%{transform:rotate(12deg)} 80%{transform:rotate(-6deg)} }
.ia-shake-hover:hover .lucide { animation: ia-shake .45s ease; transform-origin: 50% 15%; }

/* 4. Pop scale on hover — CheckCircle, Star, Heart */
.ia-pop .lucide { transition: transform .15s ease; }
.ia-pop:hover .lucide { transform: scale(1.22); transition: transform .18s cubic-bezier(.34,1.56,.64,1); }

/* 5. Draw stroke on mount — Sparkles, Zap, Check */
@keyframes ia-draw { from{stroke-dashoffset:60} to{stroke-dashoffset:0} }
.ia-draw .lucide path, .ia-draw .lucide polyline,
.ia-draw .lucide line, .ia-draw .lucide circle {
  stroke-dasharray: 60; animation: ia-draw .65s ease forwards;
}

/* 6. Bounce loop — ArrowRight, ChevronRight */
@keyframes ia-bounce-x { 0%,100%{transform:translateX(0)} 50%{transform:translateX(3px)} }
.ia-bounce-x .lucide { animation: ia-bounce-x 1.8s ease-in-out infinite; }

/* 7. Pulse scale loop — Cpu, Activity, live indicators */
@keyframes ia-pscale { 0%,100%{transform:scale(1)} 50%{transform:scale(1.2)} }
.ia-pscale .lucide { animation: ia-pscale 2s ease-in-out infinite; }
```

Usage:
```jsx
// Always-on loop
<div className="icon-box ia-float">
  <Cloud size={16} className="lucide" strokeWidth={1.75} />
</div>

// Hover trigger
<div className="icon-box ia-spin-hover cursor-default">
  <RefreshCw size={16} className="lucide" strokeWidth={1.75} />
</div>

// Bouncing arrow in button
<Button className="gap-2">
  Start free
  <span className="ia-bounce-x"><ArrowRight size={14} className="lucide" /></span>
</Button>
```

## Per-framework lucide packages

| Framework | Package |
|---|---|
| React | `lucide-react` |
| Vue 3 | `lucide-vue-next` |
| Svelte | `lucide-svelte` |
| Solid | `@lucide/solid` |
| Vanilla | Copy SVG from [lucide.dev](https://lucide.dev), add `class="lucide"` |
