---
title: Reinstall Dependencies of a NodeJS project
description: This workflow removes node_modules, clears the cache, and installs dependencies
---

### Workflow Execution Rules

- Assume current directory is project root
- Always strictly follow the steps defined in the workflow file
- Do not perform or suggest any extra steps
- If a step is skipped or cancelled, do not ask for confirmation, simply proceed to next step
- Detect package manager by checking for lockfiles in this priority order: pnpm-lock.yaml, yarn.lock, package-lock.json
- If no lockfile is found, default to npm

### Step 1: Remove node_modules

```bash
rm -rf node_modules
```

### Step 2: Clear cache (based on detected package manager)

```bash
# For pnpm projects (if pnpm-lock.yaml exists)
pnpm store prune

# For yarn projects (if yarn.lock exists)
yarn cache clean

# For npm projects (if package-lock.json exists or no lockfile)
npm cache clean --force
```

### Step 3: Install dependencies (based on detected package manager)

```bash
# For pnpm projects (if pnpm-lock.yaml exists)
pnpm install

# For yarn projects (if yarn.lock exists)
yarn install

# For npm projects (if package-lock.json exists or no lockfile)
npm install
```

### Step 4: Check if the node_modules is present

```bash
ls -ld node_modules 2>/dev/null && echo "✅ node_modules exists" || echo "❌ node_modules not found"
```
