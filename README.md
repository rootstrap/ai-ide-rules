# AI IDE Rules – Shared Repository

This repository contains standardized rule definitions for AI-powered IDEs such as **Cursor** and **Windsurf**, designed to ensure consistent, high-quality code assistance across all teams and projects at Rootstrap.

> See also:
>
> - [Rootstrap Tech Guides](https://github.com/rootstrap/tech-guides/tree/master)

## Table of Contents

- [1. About this repository](#1-about-this-repository)
- [2. Rule Hierarchy recommendation for your project](#2-rule-hierarchy-recommendation-for-your-project)
  - [2.1 Global (Team-Wide)](#21-global-team-wide)
  - [2.2 Technology-Specific](#22-technology-specific)
  - [2.3 Project-Specific](#23-project-specific)
  - [2.4 User-Specific](#24-user-specific)
- [3. What to Commit to the Project Repository](#3-what-to-commit-to-the-project-repository)
- [4. Setting Up AI IDE Rules](#4-setting-up-ai-ide-rules)
  - [4.1 Cursor Setup](#41-cursor-setup)
  - [4.2 Cursor Rule Modes](#42-cursor-rule-modes)
  - [4.3 Windsurf Setup](#43-windsurf-setup)
- [5. Contributing](#5-contributing)
- [6. TODOs](#6-todos)
- [7. Why Use AI IDE Rules?](#7-why-use-ai-ide-rules)

---

## 1. About this repository

The idea behind this repository is that each community can manage, maintain, and update its own set of rules, including ideas for the global rules.
You can collaborate by working within the `rule-templates` folder, where you will find the following structure:
```
global/
  └── base-rules.mdc
react/
  └── base-rules.mdc
  └── components/
  |   └── a11y-rules.mdc
ruby/
  └── ...
private
  └── ...
---
```
check out the **global** rules as well as the ones related to the **techs you are working on** to get you started. Once we’ve defined the global and tech rules, we can move on to the next section to apply them to our project.


## 2. Rule Hierarchy recommendation for your project

Below we define rules across **four levels** for clarity, control, and override logic, you can take this approach to set the rules in your project:

```
rules/
  └── global/
  |   └── base-rules.mdc
  └── {tech}/
  |   └── base-rules.mdc
  └── project/
  |   └── base-rules.mdc
  └── private/
       └── base-rules.mdc
---
```

For an example of how this may look on a real project you can check out the [project-example](https://github.com/rootstrap/ai-ide-rules/tree/main/project-example) folder.

### 2.1 Global (Team-Wide)

**Purpose:** Enforce universal coding norms and AI behavior across all Rootstrap projects and techs.

**Path:**

- Cursor: `.cursor/rules/global/base.rules.mdc`
- Windsurf: (Mirror global setup where applicable)

**Commit:** Yes

**Examples:**

- **Agent Persona:**
  - _You are an expert AI software engineer focused on scalable and maintainable systems in React/TypeScript._
  - Always modularize long functions/files.
  - Don’t refactor existing code without prompting.
- **Debugging Heuristics:**
  - Prioritize identifying issue roots.
  - Narrow down to 1–2 likely causes before suggesting fixes.

---

### 2.2 Tech-Level (Language/Framework Specific)

**Purpose:** Tailor AI assistance to specific ecosystems (e.g., React, Rails, Python).

**Path:**

- Cursor: `.cursor/rules/{tech}/base.rules.mdc` (or tech-specific like `react.rules.mdc`)
- Windsurf: Same structure mirrored as possible

**Scoping:** If you have multiple techs on your repository try using the `automatically attach` config with correct `globs` so it only applies to the correct files.

**Commit:** Yes

**Examples:**

- React component structure
- Python file formatting
- Rails naming conventions

---

### 2.3 Project-Specific

**Purpose:** Define rules for domain-specific constraints, module layout, naming conventions, or third-party API patterns.

**Path:**

- Cursor: `.cursor/rules/project/base.rules.mdc`
- Windsurf: Project-level equivalent
- Linters/CI config should complement these

**Scoping:** Make use of the rule scoping config to restrict when the rule should be applied. It can be:

- `Always`
- `Automatically Attached`: Here you specify `globs` (file name pattern matching)
- `Agent Requested`: Specify a `description` to help the agent know when the rule should be attached.
- `Manual`: Select this if the rule is used very specifically and it is easier to mention it when needed

Good scoping is crucial so you are not adding unnecessary context to the AI that bloats the request size and can muddy the intention of the request.

**Commit:** Yes

**Examples:**

- Specific file naming in `services/api`
- Preferred structure for `/useCases/` directory
- Required typing strategy (e.g., strict types vs loose inference)

---

### 2.4 Personal (Developer Preferences)

**Purpose:** Allow personal customizations that don’t interfere with shared rules (e.g., tab size, preferred AI styles).

**Path:**

- Cursor: `.cursorrc` or `.cursor/rules/private/some_rule_name.rules.mdc`
- Windsurf: Per-user config files (location may vary)

**Commit:** ❌ No (local-only)

**Tips:**

- Use `.cursorrc` to define personal keybindings, prompt styles, or AI personas.
- Add `.cursor/rules/private` to `.gitignore` so everyone in your project can use that folder for private rules.
- Never override `global`, `tech`, or `project` rules in your personal file.

---

## 3. What to Commit to the Project Repository

| File/Folder                   | Commit to Repo        |
| ----------------------------- | --------------------- |
| `.cursor/rules/global/*.mdc`  | ✅ Yes                |
| `.cursor/rules/{tech}/*.mdc`  | ✅ Yes                |
| `.cursor/rules/project/*.mdc` | ✅ Yes                |
| `.cursorrc`                   | ❌ No                 |
| `.cursor/rules/private/*`     | ❌ No                 |
| Windsurf equivalents          | ✅ Yes (if supported) |

**Tips:**

- Create rule drafts as `private` and upgrade them to the correct folder once you have tested them out if they would be useful to the rest of your team

---

## 4. Setting Up AI IDE Rules

### 4.1 Cursor Setup

1. **Install [Cursor IDE](https://www.cursor.sh)**
2. Open your project folder.
3. Rules will be picked up automatically from `.cursor/rules/**`.
4. You can manually reload them from the Cursor command palette: `⇧⌘P` → `Reload AI Rules`.


### 4.2 Cursor Rule Modes

Cursor supports 4 modes that determine when rules are loaded into the AI’s context:

| Mode              | Frontmatter Setup                                           | When It's Injected                                      |
|-------------------|-------------------------------------------------------------|---------------------------------------------------------|
| **Always**        | `alwaysApply: true`, no globs or description                | Loaded at the start of **every** session                |
| **Auto Attached** | `alwaysApply: false`, `globs: <pattern>`                    | Loaded when files matching the glob are **opened**      |
| **Agent Requested** | `alwaysApply: false`, `description: "<…>"`, no globs       | Available for AI to **choose** based on description     |
| **Manual**        | `alwaysApply: false`, no globs or description               | Only loaded when explicitly referenced (e.g. `@ruleName`) |

---

🔄 **Tip:** After editing an `.mdc` rule file, you must **restart or open a new chat session** for the changes to fully take effect.


### 4.3 Windsurf Setup

1. Clone this repository into your project.
2. Ensure Windsurf is pointed to `.windsurf/rules/**` or compatible config.
3. Confirm the AI agent behavior reflects the rule hierarchy.

---

## 5. Contributing

When adding new rules:

1. Choose the correct folder: `global`, `{tech}`, or `project`.
2. Use clear and structured markdown in `.mdc` format.
3. Avoid personal preferences unless they're isolated to `.cursorrc` or the `.cursor/rules/private` folder.
4. Include examples whenever possible.

For team-wide changes, propose via PR and tag relevant maintainers.

---

## 6. TODOs

- Add Windsurf-specific mapping guide
- Include a CI check to validate rule file syntax

---

## 7. Why Use AI IDE Rules?

By aligning our tools with well-defined AI guidance, we:

- Boost development speed and accuracy
- Reduce inconsistent suggestions
- Prevent AI-driven code entropy
- Empower developers while preserving team standards
