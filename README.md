# CLAUDE.md

This repository provides **production-grade agent directives** for Claude AI, engineered to streamline development workflows, bolster code integrity, and eliminate common output errors. These principles have been battle-tested against complex, real-world development hurdles, empowering Claude to maintain peak performance even within highly intricate codebases.

---

## What This Is

**CLAUDE.md** is a set of principles and best practices that guide Claude to operate in a more efficient, consistent, and reliable manner. It addresses key issues such as:

* Context decay and memory loss during large refactors.
* Missing or inaccurate verification steps before reporting success.
* Suboptimal architectural decisions caused by default behaviors.
* Inefficiencies when handling multiple files and tasks.

By implementing **CLAUDE.md**, Claude becomes more capable, helping developers maintain high standards while working with massive codebases, multi-file changes, and complex tasks.

---

## Key Features

* **Phased Execution:** Tackle large refactors step-by-step, ensuring each phase is verified before proceeding.
* **Spec-Based Development:** Ensure clarity in implementation with detailed specs, dramatically reducing ambiguity.
* **Sub-Agent Swarming:** Distribute heavy tasks across multiple agents for parallel execution.
* **Forced Verification:** Every change is verified against type checkers, linters, and test suites before marking a task as complete.
* **File System as State:** Use the file system actively for storing intermediate states and decisions, enhancing context management.

---

## Installation

To integrate **CLAUDE.md** into your project, follow these steps:

**Option 1: Download directly using curl**
```bash
curl -o CLAUDE.md [https://raw.githubusercontent.com/Wakil18/claude-md/main/CLAUDE.md](https://raw.githubusercontent.com/Wakil18/claude-md/main/CLAUDE.md)
```

**Option 2: Clone and copy**
```bash
git clone [https://github.com/Wakil18/claude-md.git](https://github.com/Wakil18/claude-md.git)
cp claude-md/CLAUDE.md /path/to/your/project/
```

> **Note:** Claude will automatically detect `CLAUDE.md` when reading from your project root.

---

## What It Solves

| Problem | Solution |
| :--- | :--- |
| **Frequent type errors** | **Forced Verification** ensures no errors remain before marking "Done!". |
| **Forgetting key context across file changes** | **Sub-Agent Swarming** ensures tasks are broken into smaller, more manageable chunks. |
| **"Minimal" fixes that aren't robust** | **Senior Dev Override** insists on cleaner, more maintainable code. |
| **Lack of file integrity verification** | **File Read Budget** limits file processing for better accuracy and focus. |

---

## Advanced Configuration

For advanced users, you can set specific rules per filetype using `.claude/rules/*.md`:

**Example: `.claude/rules/scripts.md`**
```yaml
---
paths:
  - "**/*.js"
  - "**/*.ts"
---
When editing scripts:
- Always run linting checks before editing.
- Refactor functions into smaller, more testable pieces.
```

These specialized rules only apply when editing specific types of files. This keeps your main `CLAUDE.md` file lean while ensuring maximum customization for each task.

You can also set up custom hooks in `~/.claude/settings.json`:

**Example: `~/.claude/settings.json`**
```json
{
  "hooks": {
    "PreBuild": [
      {
        "matcher": "Write(*.js)",
        "hooks": [
          {
            "type": "command",
            "command": "eslint \"$file\" --fix"
          }
        ]
      }
    ]
  }
}
```

---

## Credits

Developed and maintained by **[Your Team/Organization Name]**.

For further inquiries or collaboration, reach out via **[your contact info]**.
