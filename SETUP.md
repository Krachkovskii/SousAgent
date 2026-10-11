# Setup

Your profile contains personal (and health-related) information, so it should live in
a **private** repository. GitHub forks of public repositories are always public, so
instead of forking you create a private copy that can still receive template updates.

## 1. Create your private copy

1. On GitHub, create a new **private** repository (e.g. `my-sous-agent`).
   Leave it empty: no README, no license, no .gitignore.
2. On your computer, run:

   ```sh
   git clone https://github.com/Krachkovskii/SousAgent.git my-sous-agent
   cd my-sous-agent
   git remote rename origin upstream
   git remote add origin https://github.com/<your-username>/my-sous-agent.git
   git push -u origin main
   ```

   `upstream` is the public template (where updates come from).
   `origin` is your private copy (where your profile is saved).

3. Allow your profile to be saved by deleting `profile/.gitignore`:

   ```sh
   git rm profile/.gitignore
   git commit -m "Track profile in private copy"
   git push
   ```

   The onboarding skill will offer to do this step for you if you skip it.

## 2. Start using it

Open the folder with your AI agent and say hi. The `onboarding` skill will interview
you and create your profile. You can stop at any point and continue later.

## 3. Getting template updates

Ask the agent to *"update the template"*. The `template-update` skill gets the latest
version, checks [CHANGELOG.md](CHANGELOG.md) for changes to the profile format, and
updates your files if needed.

To do it by hand:

```sh
git pull upstream main
git push
```
