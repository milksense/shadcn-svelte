---
title: Examples
description: "Examples of registry items: styles, components, css vars, etc."
---

## registry:style

### Custom style that extends shadcn-svelte

The following registry item is a custom style that extends shadcn/ui. On `npx shadcn-svelte@latest init`, it will:

- Install `phosphor-svelte` icons as a dependency.
- Add the `login-01` block and `calendar` component to the project.
- Add the `editor` from a remote registry.
- Set the `font-sans` variable to `Inter, sans-serif`.
- Install a `brand` color in light and dark mode.

```json title="example-style.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "example-style",
  "type": "registry:style",
  "dependencies": ["phosphor-svelte"],
  "registryDependencies": [
    "login-01",
    "calendar",
    "https://example.com/r/editor.json"
  ],
  "cssVars": {
    "theme": {
      "font-sans": "Inter, sans-serif"
    },
    "light": {
      "brand": "oklch(0.145 0 0)"
    },
    "dark": {
      "brand": "oklch(0.145 0 0)"
    }
  }
}
```

### Custom style from scratch

The following registry item is a custom style that _doesn't_ extend shadcn-svelte. See the `extends: none` field.

It can be used to create a new style from scratch i.e. custom components, css vars, dependencies, etc.

On `npx shadcn-svelte@latest add`, the following will:

- Install `tailwind-merge` and `clsx` as dependencies.
- Add the `utils` registry item from the shadcn-svelte registry.
- Add the `button`, `input`, `label`, and `select` components from a remote registry.
- Install new css vars: `main`, `bg`, `border`, `text`, `ring`.

```json title="example-style.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "extends": "none",
  "name": "new-style",
  "type": "registry:style",
  "dependencies": ["tailwind-merge", "clsx"],
  "registryDependencies": [
    "utils",
    "https://example.com/r/button.json",
    "https://example.com/r/input.json",
    "https://example.com/r/label.json",
    "https://example.com/r/select.json"
  ],
  "cssVars": {
    "theme": {
      "font-sans": "Inter, sans-serif",
    }
    "light": {
      "main": "#88aaee",
      "bg": "#dfe5f2",
      "border": "#000",
      "text": "#000",
      "ring": "#000",
    },
    "dark": {
      "main": "#88aaee",
      "bg": "#272933",
      "border": "#000",
      "text": "#e6e6e6",
      "ring": "#fff",
    }
  }
}
```

## registry:theme

### Custom theme

```json title="example-theme.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-theme",
  "type": "registry:theme",
  "cssVars": {
    "light": {
      "background": "oklch(1 0 0)",
      "foreground": "oklch(0.141 0.005 285.823)",
      "primary": "oklch(0.546 0.245 262.881)",
      "primary-foreground": "oklch(0.97 0.014 254.604)",
      "ring": "oklch(0.746 0.16 232.661)",
      "sidebar-primary": "oklch(0.546 0.245 262.881)",
      "sidebar-primary-foreground": "oklch(0.97 0.014 254.604)",
      "sidebar-ring": "oklch(0.746 0.16 232.661)"
    },
    "dark": {
      "background": "oklch(1 0 0)",
      "foreground": "oklch(0.141 0.005 285.823)",
      "primary": "oklch(0.707 0.165 254.624)",
      "primary-foreground": "oklch(0.97 0.014 254.604)",
      "ring": "oklch(0.707 0.165 254.624)",
      "sidebar-primary": "oklch(0.707 0.165 254.624)",
      "sidebar-primary-foreground": "oklch(0.97 0.014 254.604)",
      "sidebar-ring": "oklch(0.707 0.165 254.624)"
    }
  }
}
```

### Custom colors

The following style will init using shadcn-svelte defaults and then add a custom `brand` color.

```json title="example-style.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-style",
  "type": "registry:style",
  "cssVars": {
    "light": {
      "brand": "oklch(0.99 0.00 0)"
    },
    "dark": {
      "brand": "oklch(0.14 0.00 286)"
    }
  }
}
```

## registry:block

### Custom block

This blocks installs the `login-01` block from the shadcn-svelte registry.

```json title="login-01.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "login-01",
  "type": "registry:block",
  "description": "A simple login form.",
  "registryDependencies": ["button", "card", "input", "label"],
  "files": [
    {
      "path": "blocks/login-01/page.svelte",
      "content": "import { LoginForm } ...",
      "type": "registry:page",
      "target": "src/routes/login/+page.svelte"
    },
    {
      "path": "blocks/login-01/components/login-form.svelte",
      "content": "...",
      "type": "registry:component"
    }
  ]
}
```

### Install a block and override primitives

You can install a block from the shadcn-svelte registry and override the primitives using your custom ones.

On `npx shadcn-svelte@latest add`, the following will:

- Add the `login-01` block from the shadcn-svelte registry.
- Override the `button`, `input`, and `label` primitives with the ones from the remote registry.

```json title="example-style.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-login",
  "type": "registry:block",
  "registryDependencies": [
    "login-01",
    "https://example.com/r/button.json",
    "https://example.com/r/input.json",
    "https://example.com/r/label.json"
  ]
}
```

## CSS Variables

### Custom Theme Variables

Add custom theme variables to the `theme` object.

```json title="example-theme.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-theme",
  "type": "registry:theme",
  "cssVars": {
    "theme": {
      "font-heading": "Inter, sans-serif",
      "shadow-card": "0 0 0 1px rgba(0, 0, 0, 0.1)"
    }
  }
}
```

### Override Tailwind CSS variables

```json title="example-theme.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-theme",
  "type": "registry:theme",
  "cssVars": {
    "theme": {
      "spacing": "0.2rem",
      "breakpoint-sm": "640px",
      "breakpoint-md": "768px",
      "breakpoint-lg": "1024px",
      "breakpoint-xl": "1280px",
      "breakpoint-2xl": "1536px"
    }
  }
}
```

## Add custom CSS

### Base styles

```json title="example-base.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-style",
  "type": "registry:style",
  "css": {
    "@layer base": {
      "h1": {
        "font-size": "var(--text-2xl)"
      },
      "h2": {
        "font-size": "var(--text-xl)"
      }
    }
  }
}
```

### Components

```json title="example-card.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-card",
  "type": "registry:component",
  "css": {
    "@layer components": {
      "card": {
        "background-color": "var(--color-white)",
        "border-radius": "var(--rounded-lg)",
        "padding": "var(--spacing-6)",
        "box-shadow": "var(--shadow-xl)"
      }
    }
  }
}
```

## Add custom utilities

### Simple utility

```json title="example-component.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-component",
  "type": "registry:component",
  "css": {
    "@utility content-auto": {
      "content-visibility": "auto"
    }
  }
}
```

### Complex utility

```json title="example-utility.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-component",
  "type": "registry:component",
  "css": {
    "@utility scrollbar-hidden": {
      "scrollbar-hidden": {
        "&::-webkit-scrollbar": {
          "display": "none"
        }
      }
    }
  }
}
```

### Functional utilities

```json title="example-functional.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-component",
  "type": "registry:component",
  "css": {
    "@utility tab-*": {
      "tab-size": "var(--tab-size-*)"
    }
  }
}
```

## Add custom animations

Note: you need to define both `@keyframes` in css and `theme` in cssVars to use animations.

```json title="example-component.json" showLineNumbers
{
  "$schema": "https://shadcn-svelte.com/schema/registry-item.json",
  "name": "custom-component",
  "type": "registry:component",
  "cssVars": {
    "theme": {
      "--animate-wiggle": "wiggle 1s ease-in-out infinite"
    }
  },
  "css": {
    "@keyframes wiggle": {
      "0%, 100%": {
        "transform": "rotate(-3deg)"
      },
      "50%": {
        "transform": "rotate(3deg)"
      }
    }
  }
}
```
