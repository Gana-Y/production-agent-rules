# ⚡ Production AI Agent Instructions & `.cursorrules` Vault

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Cursor Compatible](https://img.shields.io/badge/Cursor-Compatible-purple.svg)]()
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-orange.svg)]()
[![Copilot Instructions](https://img.shields.io/badge/Copilot-Compatible-blue.svg)]()

> A battle-tested collection of production-grade system prompts, rules, and `.cursorrules` for Cursor, Claude Code, GitHub Copilot, and coding agents. Stop getting sloppy, hallucinated, or unmaintainable AI code.

---

## 🎯 Why This Vault Exists

By default, LLM coding assistants act like enthusiastic junior developers:
* They omit critical type annotations.
* They write `except Exception: pass` and swallow bugs silently.
* They use `any` everywhere in TypeScript.
* They generate code that only works on the happy path, completely missing memory leaks, race conditions, and boundary edge cases.

This repository provides **strict, opinionated engineering rules** that force your AI assistant to think, write, and verify code like a Staff/Senior Engineer.

---

## 📦 What's Inside

| Rule File | Target Stack / Purpose | Key Enforcements |
| :--- | :--- | :--- |
| **[`python-fastapi-senior.mdc`](rules/python-fastapi-senior.mdc)** | Python 3.11+, FastAPI, Pydantic v2 | Strict types, async DB sessions, explicit HTTP exceptions, zero mutable default arguments, no wildcard imports. |
| **[`react-typescript-clean.mdc`](rules/react-typescript-clean.mdc)** | React 18+, TypeScript, Tailwind CSS | Zero `any`, strict prop interfaces, clean custom hooks, proper `useEffect` dependency hygiene, modular components. |
| **[`sql-postgresql-architect.mdc`](rules/sql-postgresql-architect.mdc)** | PostgreSQL, SQLAlchemy, Raw SQL | 3NF normalization, foreign key indexes, avoiding `SELECT *`, query plan profiling (`EXPLAIN ANALYZE`), snake_case standards. |
| **[`dsa-edge-case-tester.mdc`](rules/dsa-edge-case-tester.mdc)** | Codility, LeetCode, Algorithm Testing | Forces the AI to generate brutal adversarial test cases ($N=0, 1, 10^5$, duplicates, integer overflow) before writing the solution. |
| **[`system-design-architect.mdc`](rules/system-design-architect.mdc)** | Distributed Systems & Backends | Idempotency keys, rate limiting, Cache-Aside pattern, connection pooling, graceful shutdown handlers. |

---

## 🚀 Quick Setup (Choose Your Tool)

### 1. In Cursor
* **Option A (New Modular Rules):** Copy any `.mdc` file from the [`rules/`](rules/) directory into your project's `.cursor/rules/` folder:
  ```bash
  mkdir -p .cursor/rules
  cp rules/python-fastapi-senior.mdc .cursor/rules/
  ```
* **Option B (Root `.cursorrules`):** Copy the text from any rule directly into a `.cursorrules` file in your project root.

### 2. In Claude Code
Copy [`configs/CLAUDE.md`](configs/CLAUDE.md) into the root of your project directory. Claude Code will automatically read and adhere to it on every turn.

### 3. In GitHub Copilot
Copy [`configs/copilot-instructions.md`](configs/copilot-instructions.md) to `.github/copilot-instructions.md` in your repository.

---

## 🛠 Rule Previews

### Example: DSA Edge-Case Tester Rule
When pasted into your assistant, instead of instantly writing code, the AI is constrained by:
> *"Before providing the algorithmic solution, you MUST first produce a test matrix with at least 5 hostile corner cases: (1) Empty / null input, (2) Single-element input, (3) All negative or zero values, (4) All duplicate values, (5) Maximum boundary size ($N=10^5$) to evaluate time complexity."*

### Example: Senior Python / FastAPI Rule
> *"Never catch bare exceptions (`except:` or `except Exception:`). Always catch specific errors. All async endpoints must use dependency injection for database sessions. Every response must be validated via an explicit Pydantic `response_model`."*

---

## 🤝 Contributing
Have a bulletproof rule for Go, Rust, Flutter, or Next.js?
1. Fork this repository.
2. Add your rule file in the `rules/` directory following the `.mdc` frontmatter convention.
3. Open a Pull Request!

---

## 📄 License
MIT License. See [LICENSE](LICENSE) for details.
