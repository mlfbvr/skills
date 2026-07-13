---
name: react-bootstrap
description: Bootstrap a new React application with Vite, TypeScript, TailwindCSS, Vitest, ESLint, and Prettier.
compatibility: opencode
command: react-bootstrap
---

## What I do

- Create a new React application using Vite with TypeScript
- Configure TailwindCSS using the official Vite plugin
- Set up Vitest for testing
- Configure ESLint (from Vite template) and Prettier
- Install all dependencies
- Provide a summary of what was created

## When to use me

Use this when asked to create a new React application or bootstrap a React project.

## Prerequisites

- Node.js installed
- pnpm (preferred) or npm available

## Detection Logic

Before creating a new app, I check if a React application already exists:

1. Check if `package.json` exists and contains `react` in dependencies or devDependencies
2. Check if `src/App.tsx` or `src/App.jsx` exists

If a React app is detected, I stop and inform you with details of what was found.

## Creation Process

### 1. Detect package manager

```bash
if command -v pnpm &> /dev/null; then
    PACKAGE_MANAGER="pnpm"
else
    PACKAGE_MANAGER="npm"
fi
```

### 2. Create Vite project

```bash
$PACKAGE_MANAGER create vite . --template react-ts
```

### 3. Add TailwindCSS

```bash
$PACKAGE_MANAGER add -D @tailwindcss/vite
```

Update `vite.config.ts` to include the TailwindCSS plugin:

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [react(), tailwindcss()],
})
```

Update `src/index.css` to import TailwindCSS:

```css
@import "tailwindcss";
```

### 4. Add Vitest

```bash
$PACKAGE_MANAGER add -D vitest @testing-library/react @testing-library/jest-dom jsdom
```

Add test script to `package.json`:

```json
{
  "scripts": {
    "test": "vitest",
    "test:ui": "vitest --ui"
  }
}
```

Create `vitest.config.ts`:

```typescript
import { defineConfig } from 'vitest/config'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: './src/test/setup.ts',
    css: true,
  },
})
```

Create `src/test/setup.ts`:

```typescript
import '@testing-library/jest-dom'
```

### 5. Add Prettier

```bash
$PACKAGE_MANAGER add -D prettier
```

Create `.prettierrc`:

```json
{
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 80
}
```

Create `.prettierignore`:

```
node_modules
dist
coverage
```

### 6. Install dependencies

```bash
$PACKAGE_MANAGER install
```

## What I do NOT do

- Start the development server (`pnpm dev` or `npm run dev`)
- Create git commits
- Initialize a new git repository

## Post-Creation Summary

After creating the app, I provide:

1. **Files created**: List of key files and directories
2. **Tools installed**: Vite, React, TypeScript, TailwindCSS, Vitest, ESLint, Prettier
3. **Next steps**: How to start development (`pnpm dev`)

## Example Output

```
✅ React app created successfully!

Files created:
- src/App.tsx (main component)
- src/main.tsx (entry point)
- src/index.css (with TailwindCSS)
- vite.config.ts (with TailwindCSS plugin)
- vitest.config.ts (test configuration)
- src/test/setup.ts (test setup)
- .prettierrc (Prettier config)
- .prettierignore (Prettier ignore)

Tools installed:
- Vite (build tool)
- React 18+ (UI library)
- TypeScript (type safety)
- TailwindCSS (utility-first CSS)
- Vitest (testing framework)
- ESLint (linting)
- Prettier (code formatting)

Next steps:
- Run `pnpm dev` to start development
- Run `pnpm test` to run tests
- Run `pnpm format` to format code (add script to package.json)
```

## Quality Checklist

Before presenting the created app, verify:

- [ ] React app detected or created successfully
- [ ] TypeScript template used
- [ ] TailwindCSS configured with Vite plugin
- [ ] Vitest configured and ready
- [ ] ESLint and Prettier configured
- [ ] All dependencies installed
- [ ] Development server not started
- [ ] Summary provided to user
