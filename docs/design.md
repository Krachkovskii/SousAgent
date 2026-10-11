# Design

Decisions and reasoning behind SousAgent. Update this when a decision changes.

## Purpose

A cooking assistant for people who enjoy cooking. It manages the *context* of
cooking — pantry, equipment, people, places, restrictions, preferences — and helps
across cooking scenarios. Out of scope (for now): meal planning, shopping lists,
nutrition.

## Principles

- **Tool-neutral.** `SKILL.md` skills + plain Markdown. `AGENTS.md` is the entry
  point; `CLAUDE.md` just imports it.
- **Template is public, profile is private.** Users make a private copy with the
  public repo as `upstream` (GitHub forks of public repos can't be private).
  `profile/.gitignore` keeps data out of the template; the private copy deletes it.
- **No version control jargon** in conversations. The agent saves and syncs on its own.
- **Structured Markdown** for profile files — editable by hand, readable by models.
  YAML was rejected as too hard to edit.

## Session context

Four dimensions, each with defaults in `profile/settings.md`:

- **People** — restrictions, preferences, skill level. Not just the user: household,
  friends.
- **Kitchens** — equipment and pantry per location (home, a friend's place, a second
  home).
- **Region** — affects ingredient availability. Separate from kitchen, which may set
  a default region.
- **Scenario** — quick, exploration, crowd, use-it-up, impress, comfort.

## Restrictions vs. preferences

Split by *agent behavior*, not severity. Restrictions (allergy, with severity;
intolerance) get hidden-source checks and warnings even on explicit request.
Preferences (dislike, avoid, love) are defaults that can be bent.

No generic hidden-source list: it can't be complete and personal exceptions vary
(e.g. sunflower seeds vs. refined sunflower oil). The model uses its own knowledge;
per-person known sources and exceptions live in the person's file.

## Pantry

Six sections, from most to least reliable: stocked staples, cooking beverages,
sauces, spices, usual perishables, check-before-cooking (perishables, seasonal).
The pantry is assumed to be approximate.

## Equipment

As detailed as useful. When something is added, the agent works out which details
matter (e.g. pot: material, diameter, volume, lid, oven-safe) and asks for the
missing ones.

## Time estimates

Always two numbers:
- **Total** — start to finish, including soaking, marinating, resting, preheating.
- **Active** — chopping, stirring, watching.

`profile/log.md` records estimated vs. actual time, so estimates can be calibrated.

## Onboarding

Resumable interview. Progress is kept in `profile/onboarding.md`. Asks language and
units first.

## Versioning

Releases are git tags. `CHANGELOG.md` has a **Profile changes** section per version;
`profile/settings.md` records the template version the profile was last migrated to.
The `template-update` skill pulls updates and migrates.
