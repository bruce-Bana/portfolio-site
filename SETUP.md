# BanaChat setup and deployment

## A. Configure Firebase (free Spark plan)
1. Create a project at https://console.firebase.google.com/.
2. Open **Build → Authentication → Sign-in method** and enable **Anonymous**.
3. Create a **Realtime Database** in a nearby location.
4. In **Project settings → General → Your apps**, register a Web app and copy its config values into `firebase-config.js`.
5. Copy `database.rules.json` into Realtime Database → Rules and click **Publish**.
6. In Authentication → Settings → Authorized domains, add `bruce-bana.github.io` (no protocol and no path).

Firebase web config is intended to be visible in a client app. Never commit service-account keys or Admin SDK secrets.

## B. Publish on GitHub Pages
1. Open this repository's **Settings → Pages**.
2. Choose **Deploy from a branch**.
3. Choose branch `main` and folder `/(root)`, then Save.
4. Wait for GitHub's deployment to finish. The project URL should be:
   https://bruce-bana.github.io/portfolio-site/

## C. Test
- Firebase config placeholders are replaced with real values.
- Anonymous sign-in is enabled.
- Realtime Database rules are published.
- Firebase authorized domain includes `bruce-bana.github.io`.
- Open the site on two devices and confirm a message appears on both.

## Security and limitations
- Guest names are not verified; another visitor can impersonate a name.
- Messages are public; don't post private or sensitive information.
- Rules validate message ownership and fields, but client-side cooldowns are not robust anti-spam. Add moderation and stronger rate-limiting before a large public launch.
- The current rules allow ASCII display names. Use letters A–Z, numbers, spaces, dots, dashes, or underscores.
- Firebase free quotas apply. Review https://firebase.google.com/pricing.
- Do not use permissive database rules such as `.read: true` or `.write: true`.

## Troubleshooting
- **Setup required:** replace placeholders in `firebase-config.js`.
- **unauthorized-domain:** add `bruce-bana.github.io` to Firebase Authentication authorized domains.
- **Permission denied:** enable Anonymous sign-in and publish `database.rules.json`.
- **No module loads:** access through GitHub Pages or an HTTP server, not by double-clicking the HTML file.