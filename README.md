# Lisaany — Learn Arabic · Android (Capacitor)

`www/index.html` is BOTH the website and the app. Edit it on GitHub as always.

## Two kinds of update
| You changed…            | What happens                                              | Store upload? |
|-------------------------|-----------------------------------------------------------|---------------|
| Lessons, text, design   | Workflow 3 pushes it to installed apps within minutes (Capgo) | No |
| Icon, name, native plugin, new platform | Workflow 2 builds a new .aab → upload to Play Console | Yes |

## One-time setup (browser only)
1. Upload this folder to a new GitHub repo (keep `.github`, `www`, `resources`).
2. Actions → "1) Create signing key" → Run. Download the artifact; keep the `.keystore` forever; open `secrets.txt`.
3. Settings → Secrets → Actions → add `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`.
4. Capgo (free): capgo.app → sign up → Add app → App ID `com.lisaany.arabic`, name Lisaany.
   Settings → API keys → create an "upload" key → add it as GitHub secret `CAPGO_TOKEN`.
   In the app's Channels, make sure `production` exists and is the default.
5. Actions → "2) Build Android" → Run → download `lisaany-android-aab` → upload to Play Console.
6. Actions → "3) Live update" → Run once so Capgo has the first bundle.

From then on: every commit to `www/` runs workflow 3 automatically. Installed apps pick up the new
content on their next launch. Workflow 2 also runs, but you only need its .aab for native changes.

## Note on audio
Inside the app the page runs from `https://localhost`. If your R2 bucket's CORS rule lists specific
origins, add `https://localhost`.
