---
name: cook
description: Suggest dishes and guide cooking within the user's restrictions, preferences, equipment, pantry and region. Use when the user wants ideas, a recipe, or help with something they're cooking. Supports combinable scenarios - quick, exploration, crowd, use-it-up, impress, comfort.
---

# Cook

Help the user pick a dish and cook it. Keep questions to a minimum: ask only what
changes the suggestions, and use defaults for everything else.

## 1. Context

Establish five things. Take them from the request, then from `profile/settings.md`
defaults. Mention defaults you assumed in one line, don't ask about them.

- **Who's eating:** load each person's file from `profile/people/`. Guests not in
  the profile: ask about allergies and intolerances.
- **Kitchen:** load its `equipment.md` and `pantry.md`.
- **Region:** what's realistically available.
- **Scenario(s):** from `scenarios/`. If none fits, cook without one.
- **Shopping:** whether the user can buy things. Each scenario sets its default.

## 2. Scenarios

Load every scenario that applies. They combine (quick + crowd, comfort + quick,
impress + crowd). When they conflict, this order wins:

1. Restrictions (AGENTS.md › Safety rules).
2. Equipment — what the kitchen physically can't do.
3. Explicit limits from the user (time, head count, no shopping).
4. Scenario goals (novelty, impressiveness, using things up).
5. Preferences.

If the combination leaves nothing reasonable, say so and say which constraint to
relax.

## 3. Overview

Offer **3–5 dishes**, short enough to choose by vibe. For each:

- **Name**
- **One-line description**
- **Scenario-specific details**, as each scenario file defines under
  *In the overview*. For combined scenarios, include each one's details.
- **Flags**, only when relevant: a restriction that needs a substitution, missing
  ingredients, equipment workarounds.

No full recipes, no long explanations at this stage.

## 4. Recipe

Once the user picks a dish, clarify only details that change the recipe (e.g.
quantities, condition of an ingredient), then give:

- **Times:** total and active, per [references/time-estimation.md](references/time-estimation.md).
- **Ingredients** with quantities, in the user's units. Mark what isn't in the
  pantry or needs checking.
- **Equipment** to use, from this kitchen.
- **Steps** as an order of work, with parallel steps where possible.
- **Safety notes:** substitutions made for restrictions, and why.
- Anything the scenario files add (plating, teaching, yield, batches).

## 5. Afterwards

When the user reports back: log the dish, techniques and actual time in
`profile/log.md`, and offer pantry updates via `profile-update`.
