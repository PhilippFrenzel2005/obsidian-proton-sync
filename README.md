# Proton Drive Sync (Obsidian Plugin)

This is an Obsidian community plugin that will enable syncing vault files with Proton Drive.

## Development

- Install dependencies.
- Start the development build (watch mode).

### Code quality

- Run lint checks: `npm run lint`
- Auto-fix lint issues: `npm run lint:fix`
- Check formatting: `npm run format:check`
- Apply formatting: `npm run format`
- Run all checks (lint + format + tests): `npm run check`

The build outputs `main.js`, which Obsidian loads.

## Loading the plugin in Obsidian

Copy this folder into your vault at:

`.obsidian/plugins/proton-drive-sync`

Then enable the plugin in **Settings → Community plugins**.

## Human verification during login

When Proton requires a CAPTCHA, choose **Open CAPTCHA in browser** in the
plugin's verification dialog. Complete verification on `https://verify.proton.me/`,
then return to Obsidian and choose **I completed verification — Continue**.
Keep the dialog open while verifying. Two-factor authentication follows when
required by the account; do not disable it.

This uses Proton's external-browser verification flow, rather than embedding its
page in an iframe. The browser submits the solution to Proton; the plugin retries
the original login once with the challenge token. Clicking Continue without
successful verification cannot authorize login. If Proton rejects the retry,
reconnect to request a fresh challenge. Cancel closes the attempt without retrying.

Initial authentication requests time out after 30 seconds. No verification URLs, passwords,
or human-verification tokens are logged by this flow. Signing in does not start
a push or pull.
