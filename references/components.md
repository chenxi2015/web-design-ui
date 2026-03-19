# Component Patterns

All components use shadcn/ui. Only className additions listed — no reinventing.

## Button

```jsx
// Default — inherits --primary token, no shadow
<Button>Get started</Button>
<Button variant="outline" className="hover:border-foreground/25 transition-colors">View docs →</Button>
<Button variant="ghost" className="text-muted-foreground hover:text-foreground">Pricing</Button>
<Button variant="secondary">Contact</Button>

// With icon (single-line import required)
<Button className="gap-1.5"><Zap size={14} className="lucide" />Deploy</Button>

// Green gradient CTA (only when green accent active)
<Button className="border-0 font-semibold text-white"
  style={{ background: "linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary) / .8))" }}>
  Get started free
</Button>
```

**Rule: never add `hover:shadow-*` to buttons.**

## Card — shadow-none mandatory

```jsx
<Card className="shadow-none border-slate-200/70 dark:border-border/70
  transition-colors duration-150
  hover:border-foreground/15 hover:bg-foreground/[0.02]">
  <CardHeader>
    {/* Icon box */}
    <div className="icon-box w-9 h-9 rounded-lg flex items-center justify-center mb-3">
      <Zap size={16} className="lucide" strokeWidth={1.75} />
    </div>
    <CardTitle className="text-sm font-semibold">Title</CardTitle>
    <CardDescription className="text-xs leading-relaxed">Description</CardDescription>
  </CardHeader>
</Card>
```

Icon box CSS (put in globals.css):
```css
.icon-box { width:36px; height:36px; border-radius:10px; display:flex; align-items:center; justify-content:center; }
.mint-light .icon-box { background: hsl(var(--primary) / .1); }
.mint-dark  .icon-box { background: hsl(var(--foreground) / .07); border: 1px solid hsl(var(--foreground) / .06); }
.icon-box .lucide { color: hsl(var(--primary)); }
```

## Badge

```jsx
// Accent — adapts to current --primary
<div className="inline-flex items-center gap-1.5 rounded-full px-3 py-1 text-xs font-medium border"
  style={{ background: "hsl(var(--primary)/.08)", color: "hsl(var(--primary))", borderColor: "hsl(var(--primary)/.22)" }}>
  <span className="w-1.5 h-1.5 rounded-full" style={{ background: "hsl(var(--primary))" }} />
  Live
</div>

// shadcn defaults
<Badge variant="secondary">Stable</Badge>
<Badge variant="outline">v2.0</Badge>
<Badge className="bg-blue-500/10 text-blue-400 border border-blue-500/20">New</Badge>
```

## Input

```jsx
// No custom styling needed — --ring token handles focus state
<div className="space-y-1.5">
  <Label className="text-xs">Project URL</Label>
  <Input placeholder="https://docs.yoursite.com" className="h-9 text-xs" />
</div>
```

## Navigation

```jsx
<header className="sticky top-0 z-50 border-b border-border/50
  bg-background/85 backdrop-blur-xl
  transition-colors duration-300">
  <div className="flex h-14 items-center justify-between px-6 max-w-5xl mx-auto">
    {/* Logo */}
    <div className="flex items-center gap-2 font-semibold text-sm">
      <div className="w-6 h-6 rounded-md bg-primary flex items-center justify-center text-primary-foreground font-black text-[10px]">
        M
      </div>
      Mintlify
    </div>
    {/* Links */}
    <nav className="flex gap-0.5">
      <Button variant="ghost" size="sm" className="text-xs text-muted-foreground h-8 hover:text-foreground">Docs</Button>
    </nav>
    {/* CTA */}
    <Button size="sm" className="text-xs h-8">Start free</Button>
  </div>
</header>
```

## Tabs with active tint

```css
/* globals.css */
[data-state=active].m-tab {
  background: hsl(var(--primary) / .09) !important;
  color: hsl(var(--primary)) !important;
}
```

```jsx
<Tabs defaultValue="overview">
  <TabsList className="bg-card border border-border">
    <TabsTrigger value="overview" className="m-tab text-xs data-[state=active]:shadow-none">Overview</TabsTrigger>
    <TabsTrigger value="code"     className="m-tab text-xs data-[state=active]:shadow-none">Code</TabsTrigger>
  </TabsList>
  <TabsContent value="overview">...</TabsContent>
</Tabs>
```

## Keyboard chip

```jsx
<kbd className="inline-flex items-center rounded border border-border bg-muted px-1.5 py-0.5 font-mono text-[11px] text-muted-foreground">
  ⌘K
</kbd>
```

## Stat card

```jsx
<Card className="shadow-none border-slate-200/70 dark:border-border/70 p-4">
  <p className="text-2xl font-bold mb-0.5 bg-clip-text text-transparent"
    style={{ backgroundImage: "linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary) / .55))", letterSpacing: "-0.03em" }}>
    2M+
  </p>
  <p className="text-xs text-muted-foreground">Monthly developers</p>
</Card>
```

## Fading divider

```jsx
<div className="h-px bg-gradient-to-r from-transparent via-border to-transparent my-12" />
```

## Section label

```jsx
<p className="text-[11px] font-semibold tracking-[0.1em] uppercase mb-2"
  style={{ color: "hsl(var(--primary))" }}>
  Features
</p>
```
