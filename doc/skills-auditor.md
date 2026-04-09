# skills-auditor registration (AK.skill)

Use this when you want the [skills-auditor](https://github.com/ERerGB/skills-auditor) CLI to **audit, dedupe, and route** this pack alongside your global Cursor/Claude skill trees.

## What gets scanned

Point **`SKILLS_AUDITOR_EXTRA_ROOTS`** at the directory that **contains** the skill folders (`paradigm-surface/`, `ak/`, …)—i.e. this repo’s **`skills/`** directory, not the repo root.

## One-shot env file

Copy or symlink:

- `config/skills-auditor.ak.env`

Then:

```bash
set -a
source ~/AK.skill/config/skills-auditor.ak.env   # adjust path if you cloned elsewhere
set +a
export SKILLS_AUDITOR_MODE=full
# Preview only: export SKILLS_AUDITOR_DRY_RUN=1
```

Run the **full pipeline** recipe from the skills-auditor `SKILL.md` (bash `case` block: discover → dedup → route → traces → sync → close).

## Minimal manual invocation

If you already have `skills-audit` on `PATH`:

```bash
AK_SKILLS="$HOME/AK.skill/skills"
skills-audit audit --skills-dir "$HOME/.cursor/skills" --skills-dir "$HOME/.claude/skills" --skills-dir "$AK_SKILLS" --with-drift
```

Replace `$HOME/AK.skill` with your clone path. **Dedup/route** with `--apply` follow the upstream skill’s default pipeline when you are not in dry-run mode.

## Note

skills-auditor **does not** install skills into `~/.cursor/skills/` by itself when there are no duplicate names. For Cursor to load **`/ak`**, still copy or symlink `skills/ak` (and siblings) per the main README Quickstart.
