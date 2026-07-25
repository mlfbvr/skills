---
name: create-next-app
description: Bootstrap a new Next.js application with TypeScript, TailwindCSS, ESLint, and App Router.
compatibility: opencode
command: create-next-app
---

## What I do

- Create a new Next.js application using `create-next-app`
- Use TypeScript, TailwindCSS, and ESLint (all included by default)
- Use the App Router (default)
- Use the `src/` directory (default)
- Install all dependencies
- Provide a summary of what was created

## When to use me

Use this when asked to create a new Next.js application or bootstrap a Next.js project.

## Prerequisites

- Node.js installed
- pnpm (preferred) or npm available

## Detection Logic

Before creating a new app, I check if a Next.js application already exists:

1. Check if `package.json` exists and contains `next` in dependencies or devDependencies
2. Check if `next.config.ts` or `next.config.js` exists

If a Next.js app is detected, I stop and inform you with details of what was found.

## Creation Process

### 1. Detect package manager

```bash
if command -v pnpm &> /dev/null; then
    PACKAGE_MANAGER="pnpm"
else
    PACKAGE_MANAGER="npm"
fi
```

### 2. Create Next.js project

```bash
$PACKAGE_MANAGER create next-app . --ts --tailwind --eslint --app --src-dir --import-alias "@/*" --use-$PACKAGE_MANAGER
```

This command handles everything:
- TypeScript configuration
- TailwindCSS setup
- ESLint configuration
- App Router (default)
- `src/` directory (default)
- Import alias (`@/*`)
- Dependency installation

## What I do NOT do

- Start the development server (`pnpm dev` or `npm run dev`)
- Create git commits
- Initialize a new git repository

## Post-Creation Summary

After creating the app, I provide:

1. **Files created**: List of key files and directories
2. **Tools installed**: Next.js, TypeScript, TailwindCSS, ESLint
3. **Next steps**: How to start development (`pnpm dev`)

## Example Output

```
Next.js app created successfully!

Files created:
- src/app/layout.tsx (root layout)
- src/app/page.tsx (home page)
- src/app/globals.css (global styles)
- next.config.ts (Next.js configuration)
- tsconfig.json (TypeScript configuration)
- tailwind.config.ts (TailwindCSS configuration)
- postcss.config.mjs (PostCSS configuration)
- eslint.config.mjs (ESLint configuration)

Tools installed:
- Next.js (React framework)
- TypeScript (type safety)
- TailwindCSS (utility-first CSS)
- ESLint (linting)

Next steps:
- Run `pnpm dev` to start development
- Open http://localhost:3000 in your browser
```

## Quality Checklist

Before presenting the created app, verify:

- [ ] Next.js app detected or created successfully
- [ ] TypeScript enabled
- [ ] TailwindCSS configured
- [ ] ESLint configured
- [ ] App Router used
- [ ] `src/` directory used
- [ ] All dependencies installed
- [ ] Development server not started
- [ ] Summary provided to user
