# Hero Gradient Presets

All gradients use `hsl(var(--primary) / opacity)` — adapt automatically when theme or accent color changes.

## 1. Mesh (most common — shadcn style)

```css
.hero-mesh { position: relative; overflow: hidden; background: hsl(var(--background)); }
.hero-mesh::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background:
    radial-gradient(ellipse 80% 60% at 20% 10%,  hsl(var(--primary) / .12) 0%, transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 20%,  hsl(var(--primary) / .07) 0%, transparent 55%),
    radial-gradient(ellipse 70% 50% at 50% 90%,  hsl(var(--primary) / .06) 0%, transparent 55%);
}
.hero-mesh::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 120px;
  background: linear-gradient(to bottom, transparent, hsl(var(--background)));
  pointer-events: none;
}
```

## 2. Radial — centered bloom + dot grid

```css
.hero-radial { position: relative; overflow: hidden; background: hsl(var(--background)); }
.hero-radial::before {
  content: ''; position: absolute; top: -30%; left: 50%; transform: translateX(-50%);
  width: 900px; height: 600px; pointer-events: none;
  background: radial-gradient(ellipse at center,
    hsl(var(--primary) / .14) 0%,
    hsl(var(--primary) / .05) 35%,
    transparent 65%);
}
.hero-radial::after {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background-image: radial-gradient(circle, hsl(var(--foreground) / .04) 1px, transparent 1px);
  background-size: 28px 28px;
}
```

## 3. Grid — CSS lines + mask fade

```css
.hero-grid { position: relative; overflow: hidden; background: hsl(var(--background)); }
.hero-grid::before {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background-image:
    linear-gradient(hsl(var(--primary) / .06) 1px, transparent 1px),
    linear-gradient(90deg, hsl(var(--primary) / .06) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse 80% 70% at 50% 30%, black 30%, transparent 75%);
  -webkit-mask-image: radial-gradient(ellipse 80% 70% at 50% 30%, black 30%, transparent 75%);
}
.hero-grid::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 160px;
  background: linear-gradient(to bottom, transparent, hsl(var(--background)));
  pointer-events: none;
}
```

## 4. Aurora — animated conic sweep

```css
@keyframes aurora-spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
.hero-aurora { position: relative; overflow: hidden; background: hsl(var(--background)); }
.hero-aurora::before {
  content: ''; position: absolute; top: -60%; left: 50%; transform: translateX(-50%);
  width: 160%; height: 200%; pointer-events: none;
  background: conic-gradient(
    from 180deg at 50% 30%,
    hsl(var(--primary) / .00)   0deg,
    hsl(var(--primary) / .10)  60deg,
    hsl(var(--primary) / .00) 120deg,
    hsl(var(--primary) / .07) 200deg,
    hsl(var(--primary) / .00) 360deg
  );
  animation: aurora-spin 18s linear infinite;
}
.hero-aurora::after {
  content: ''; position: absolute; inset: 0; pointer-events: none;
  background: radial-gradient(ellipse 100% 60% at 50% 0%, transparent 40%, hsl(var(--background)) 75%);
}
```

## Usage in JSX

```jsx
<section className="hero-mesh"> {/* or hero-radial, hero-grid, hero-aurora */}
  <div className="relative z-10 py-24 text-center">
    {/* hero content */}
  </div>
</section>
```

## Opacity scale

```
Strong   → hsl(var(--primary) / .15)
Default  → hsl(var(--primary) / .10)
Subtle   → hsl(var(--primary) / .06)
Faint    → hsl(var(--primary) / .03)
```
