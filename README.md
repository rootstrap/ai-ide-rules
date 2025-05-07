# AI IDE Rules – Shared Repository

This repository contains standardized rule definitions for AI-powered IDEs such as **Cursor** and **Windsurf**, designed to ensure consistent, high-quality code assistance across all teams and projects at Rootstrap.

We follow a **4-level hierarchy** of rules to enable scalable AI collaboration while allowing flexibility where needed.

> See also:
> - [Rootstrap Tech Guides](https://github.com/rootstrap/tech-guides/tree/master)

---

## Repository Structure

global/
  └── base-rules.mdc
react/
  └── base-rules.mdc
  └── folder/   
  |   └── language-rules.mdc
react-native/
  └── ...
ruby/
  └── ...
swift/
  └── ...
---

## 1. A Hierarchy of Rules

We define rules across **four levels** for clarity, control, and override logic:

### 1.1 Global (Team-Wide)

**Purpose:**
Enforce universal coding norms and AI behavior across all Rootstrap projects.

**Path:**
- Cursor: `.cursor/rules/global/base.rules.mdc`
- Windsurf: (Mirror global setup where applicable)

**Commit:** Yes

**Examples:**
- **Agent Persona:**
  - *You are an expert AI software engineer focused on scalable and maintainable systems in React/TypeScript.*
  - Always modularize long functions/files.
  - Don’t refactor existing code without prompting.
- **Debugging Heuristics:**
  - Prioritize identifying issue roots.
  - Narrow down to 1–2 likely causes before suggesting fixes.

---

### 1.2 Tech-Level (Language/Framework Specific)

**Purpose:**  
Tailor AI assistance to specific ecosystems (e.g., React, Rails, Python).

**Path:**  
- Cursor: `.cursor/rules/{tech}/base.rules.mdc` (or tech-specific like `react.rules.mdc`)
- Windsurf: Same structure mirrored as possible

**Scoping:**
If you have multiple techs on your repository try using the `automatically attach` config with correct `globs` so it only applies to the correct files.

**Commit:** Yes

**Examples:**
- React component structure
- Python file formatting
- Rails naming conventions

---

### 1.3 Project-Specific

**Purpose:**  
Define rules for domain-specific constraints, module layout, naming conventions, or third-party API patterns.

**Path:**  
- Cursor: `.cursor/rules/project/base.rules.mdc`
- Windsurf: Project-level equivalent
- Linters/CI config should complement these

**Scoping:**
Make use of the rule scoping config to restrict when the rule should be applied.
It can be:
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

### 1.4 Personal (Developer Preferences)

**Purpose:**  
Allow personal customizations that don’t interfere with shared rules (e.g., tab size, preferred AI styles).

**Path:**  
- Cursor: `.cursorrc` or `.cursor/rules/private/some_rule_name.rules.mdc`
- Windsurf: Per-user config files (location may vary)

**Commit:** ❌ No (local-only)

**Tips:**
- Use `.cursorrc` to define personal keybindings, prompt styles, or AI personas.
- Add `.cursor/rules/private` to `.gitignore` so everyone in your project can use that folder for private rules.
- Never override `global`, `tech`, or `project` rules in your personal file.

---

## What to Commit to the Project Repository

| File/Folder                         | Commit to Repo |
|------------------------------------|----------------|
| `.cursor/rules/global/*.mdc`       | ✅ Yes         |
| `.cursor/rules/{tech}/*.mdc`       | ✅ Yes         |
| `.cursor/rules/project/*.mdc`      | ✅ Yes         |
| `.cursorrc`                        | ❌ No          |
| `.cursor/rules/private/*`          | ❌ No          |
| Windsurf equivalents        | ✅ Yes (if supported) |

**Tips:**
- Create rule drafts as `private` and upgrade them to the correct folder once you have tested them out if they would be useful to the rest of your team
---

## Setting Up AI IDE Rules

### Cursor Setup

1. **Install [Cursor IDE](https://www.cursor.sh)**
2. Open your project folder.
3. Rules will be picked up automatically from `.cursor/rules/**`.
4. You can manually reload them from the Cursor command palette:  
   `⇧⌘P` → `Reload AI Rules`.

### Windsurf Setup

1. Clone this repository into your project.
2. Ensure Windsurf is pointed to `.windsurf/rules/**` or compatible config.
3. Confirm the AI agent behavior reflects the rule hierarchy.

---

## Contributing

When adding new rules:

1. Choose the correct folder: `global`, `{tech}`, or `project`.
2. Use clear and structured markdown in `.mdc` format.
3. Avoid personal preferences unless they're isolated to `.cursorrc` or the `.cursor/rules/private` folder.
4. Include examples whenever possible.

For team-wide changes, propose via PR and tag relevant maintainers.

---

## TODOs

- Add Windsurf-specific mapping guide
- Include a CI check to validate rule file syntax

---

## �� Why Use AI IDE Rules?

By aligning our tools with well-defined AI guidance, we:

- Boost development speed and accuracy
- Reduce inconsistent suggestions
- Prevent AI-driven code entropy
- Empower developers while preserving team standards