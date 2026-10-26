# kioskit-template-state

Starter **state repo** for [Kioskit](https://kioskit.io), your fleet's desired config.

## Setup

1. Click **Use this template** to create your own copy.
2. Connect it as your state repo in the Kioskit console. The Kioskit GitHub App needs
   **Contents: write** so it can open claim PRs.

## How it works

- Claiming a device opens a PR that adds its config under `src/devices/<primary-mac>/`.
  You don't create these folders by hand.
- **Kioskit validate** checks every device folder on each PR.
- Merging to `main` runs **Kioskit publish**, which delivers each folder to its device.
  Publish runs fail with an HTTP 403 until the repo is connected.

Both workflows call the public, signed
[kioskit-publish](https://github.com/JonathanPorta/kioskit-publish) workflow and need no
secrets.
