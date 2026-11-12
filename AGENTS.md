# Toolkit maintenance instructions

This repository contains reusable workflows, not a hackathon application. These rules govern toolkit edits, including inside a submodule; they do not govern parent-application tasks.

- Read [README](README.md), [formats](docs/FORMATS.md), and the requested maintenance scope. A human-approved maintenance request is sufficient; do not require a project PLAN or allocate project HK IDs here.
- Preserve event, project, person, sponsor, model, and stack independence. Keep the playbook consolidated and preserve useful material.
- Canonical skills live in `.agents/skills`. Generated starter adapters reference them; never maintain copied workflow bodies.
- Templates are source material, not approval. The [project contract](docs/PROJECT_CONTRACT.md) applies when adopted by project instructions or a workflow targeting that project.
- Use a feature branch; preserve existing work. Do not update a parent's submodule pin, commit, merge, tag, publish, or deploy without applicable authorization.
- Keep toolkit implementation history and verification summaries in chat or pull requests, not repository-specific task notes. Project workflows still write their project-owned notes outside the toolkit.
- Run `node --test`, `node scripts/toolkit.mjs validate`, and `git diff --check`. Test bootstrap in temporary starters and validate links and schema consistency.
- Report observed results and limits. Static validation does not prove native agent behavior or external integrations. Automatic delegation is not required.

Maintenance handoffs identify delivered behavior, checks, and limitations. Strict packaged-skill reports do not apply to ordinary toolkit maintenance conversation.
