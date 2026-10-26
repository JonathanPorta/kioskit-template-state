# kioskit-template-state

Starter **state repository** for [Kioskit](https://kioskit.io). Create your own copy
from this one with GitHub's **"Use this template"** button, then connect it as your
*state repo* in the Kioskit console.

This is your fleet's **desired-state store**. When you claim a device, Kioskit opens a
pull request here that adds the device's rendered config under
`src/devices/<primary-mac>/`. Merging that PR publishes the bundle to the device.

```
src/
  devices/
    .gitkeep        # keeps the directory tracked until your first claim
    README.md       # layout note
```

The Kioskit GitHub App needs **Contents: write** on this repo so it can open claim PRs.
You don't add device directories by hand — claiming a device creates them for you.

## Workflows

`.github/workflows/` holds two thin callers for the public, signed
[kioskit-publish](https://github.com/JonathanPorta/kioskit-publish) workflow. Neither
needs a secret.

- **Kioskit publish** runs on every push to `main` and republishes every device folder.
  It authenticates to Kioskit with the run's GitHub OIDC token. Until you connect the
  repo in the console, its runs fail with `no_trust_policy`, and that's expected.
- **Kioskit validate** runs on pull requests and checks every device folder without
  publishing. Make it a required check on `main` to block broken configs before merge.

Both are pinned to the same full commit SHA, which must be one the Kioskit Worker
allows. To move the pin, follow the kioskit-publish README's
[Upgrading](https://github.com/JonathanPorta/kioskit-publish#upgrading-the-publisher) steps.

`blessed.yml` describes this template for its maintainers' tooling, not your copy. You
can delete it from your repository.
