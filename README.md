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
