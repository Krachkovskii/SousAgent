---
name: cook
description: Suggest dishes and guide cooking within the user's restrictions, preferences, equipment, pantry and region. Use when the user wants ideas, a recipe, or help with something they're cooking. Routes to a scenario (quick, exploration, crowd, use-it-up, impress, comfort).
---

# Cook

> Stub — to be written.

Outline:
1. Establish context: who's eating, which kitchen, where, scenario (defaults from
   `profile/settings.md`).
2. Load the matching file(s) from `scenarios/`. Scenarios combine (e.g. quick +
   crowd). Restrictions always come first.
3. Apply safety rules from AGENTS.md.
4. Give time estimates per [references/time-estimation.md](references/time-estimation.md).
