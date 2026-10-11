# Profile

Your personal data lives here. In the public template, everything in this folder
except this file and `.gitignore` is ignored. See [SETUP.md](../SETUP.md).

Files are created by the `onboarding` skill and kept up to date by `profile-update`.
You can also edit them by hand.

```
profile/
├── settings.md              # language, units, defaults, template version
├── onboarding.md            # onboarding progress (so it can be resumed)
├── people/<name>.md         # restrictions, preferences, skill level
├── kitchens/<name>/
│   ├── equipment.md         # tools and appliances, with relevant details
│   └── pantry.md            # what's usually there and what needs checking
├── regions/<name>.md        # local availability notes (optional)
└── log.md                   # cooking log: dishes, techniques, estimated vs. actual time
```

## Restrictions vs. preferences

- **Restrictions** (allergies, intolerances): checked for hidden sources; the agent
  warns even when you ask for the dish yourself. Each entry can list known hidden
  sources and explicit exceptions (e.g. "sunflower seeds: allergy; refined sunflower
  oil is fine").
- **Preferences** (dislikes, avoid, love): followed by default, but can be bent —
  for example in exploration mode. Includes comfort dishes and flavors, and cooking
  habits (e.g. whether cleanup counts toward time).

Rule of thumb: *should the agent check hidden sources and warn me even when I ask
for it?* Yes → restriction. No → preference.

## Pantry sections

1. Stocked staples — grains, legumes, flours, etc.
2. Cooking beverages — wine, beer, spirits.
3. Sauces and condiments
4. Spices
5. Usual perishables — likely there, e.g. milk, eggs, hard cheese.
6. Check before cooking — perishables and seasonal items; always confirm.
