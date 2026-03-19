# Framework Agnostic Usage

## What's truly portable

| Feature | React | Vue | Svelte | Solid | HTML |
|---|---|---|---|---|---|
| CSS token layer (`globals.css`) | ✅ | ✅ | ✅ | ✅ | ✅ |
| Hero gradient presets | ✅ | ✅ | ✅ | ✅ | ✅ |
| Icon animations (CSS classes) | ✅ | ✅ | ✅ | ✅ | ✅ |
| Dark/light toggle (class swap) | ✅ | ✅ | ✅ | ✅ | ✅ |
| shadcn/ui components | ✅ | ❌ | ❌ | ❌ | ❌ |

For non-React frameworks: use the CSS token layer + native HTML elements styled with the same classes.

## globals.css — copy once, use anywhere

```css
/* Copy this into your project's global stylesheet */

.mint-light {
  --background: 0 0% 100%;  --foreground: 222 47% 11%;
  --card: 0 0% 99%;         --primary: 222 47% 11%;
  --primary-foreground: 0 0% 100%;
  --border: 214 20% 90%;    --ring: 222 47% 11%;
  --radius: 0.625rem;
  /* ... full token list in tokens-and-theming.md */
}
.mint-dark {
  --background: 0 0% 4%;   --foreground: 210 40% 97%;
  --card: 220 13% 7%;      --primary: 210 40% 97%;
  --primary-foreground: 0 0% 4%;
  --border: 220 13% 13%;   --ring: 210 40% 97%;
  /* ... */
}

/* Hero gradient */
.hero-mesh { /* ... see hero-gradients.md */ }

/* Icon animations */
.ia-float .lucide { animation: ia-float 2.6s ease-in-out infinite; }
/* ... see icons.md */
```

## Vue 3

```vue
<script setup>
// npm install lucide-vue-next
import { Zap } from 'lucide-vue-next'
const dark = ref(false)
</script>

<template>
  <div :class="dark ? 'mint-dark' : 'mint-light'" style="min-height:100vh;background:hsl(var(--background));color:hsl(var(--foreground))">
    <section class="hero-mesh">
      <div style="position:relative;z-index:1;padding:96px 0;text-align:center">
        <h1 :style="{ color: 'hsl(var(--primary))' }">Knowledge Platform</h1>
        <div class="icon-box ia-float">
          <Zap :size="16" class="lucide" />
        </div>
        <button @click="dark = !dark">Toggle</button>
      </div>
    </section>
  </div>
</template>
```

## Svelte 5

```svelte
<script>
  // npm install lucide-svelte
  import { Zap } from 'lucide-svelte'
  let dark = $state(false)
</script>

<div class={dark ? 'mint-dark' : 'mint-light'} style="min-height:100vh;background:hsl(var(--background));color:hsl(var(--foreground))">
  <section class="hero-mesh">
    <div style="position:relative;z-index:1;padding:96px 0;text-align:center">
      <h1 style="color:hsl(var(--primary))">Knowledge Platform</h1>
      <div class="icon-box ia-float">
        <Zap size={16} class="lucide" />
      </div>
      <button onclick={() => dark = !dark}>Toggle</button>
    </div>
  </section>
</div>
```

## Solid.js

```jsx
// npm install @lucide/solid
import { createSignal } from 'solid-js'
import { Zap } from '@lucide/solid'

export function App() {
  const [dark, setDark] = createSignal(false)
  return (
    <div class={dark() ? 'mint-dark' : 'mint-light'} style={{ "min-height":"100vh", background:"hsl(var(--background))", color:"hsl(var(--foreground))" }}>
      <section class="hero-mesh">
        <div style={{ position:"relative", "z-index":1, padding:"96px 0", "text-align":"center" }}>
          <h1 style={{ color:"hsl(var(--primary))" }}>Knowledge Platform</h1>
          <div class="icon-box ia-float">
            <Zap size={16} class="lucide" />
          </div>
          <button onClick={() => setDark(d => !d)}>Toggle</button>
        </div>
      </section>
    </div>
  )
}
```

## Vanilla HTML

```html
<link rel="stylesheet" href="globals.css" />

<div class="mint-light" id="root">
  <section class="hero-mesh">
    <div style="position:relative;z-index:1;padding:96px 0;text-align:center">
      <h1 style="color:hsl(var(--primary))">Knowledge Platform</h1>

      <!-- Copy SVG from lucide.dev — add class="lucide" -->
      <div class="icon-box ia-float">
        <svg class="lucide" width="16" height="16" viewBox="0 0 24 24"
          fill="none" stroke="currentColor" stroke-width="1.75"
          xmlns="http://www.w3.org/2000/svg">
          <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
        </svg>
      </div>

      <button onclick="toggleDark()">Toggle dark</button>
    </div>
  </section>
</div>

<script>
  function toggleDark() {
    const root = document.getElementById('root')
    root.className = root.className === 'mint-light' ? 'mint-dark' : 'mint-light'
  }
</script>
```
