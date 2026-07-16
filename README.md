# Vault — Static App Store (GitHub Pages)

No backend, no Firebase. Two files do everything:
- `index.html` — the storefront (design + logic)
- `apps.json` — the list of apps (this is the only file you edit to add/remove apps)

## 1. Put this online (one-time setup)

1. Go to github.com → New repository → name it anything (e.g. `vault-store`) → Public → Create.
2. Upload `index.html` and `apps.json` into it (drag-and-drop on the repo's "Add file → Upload files" page).
3. Go to **Settings → Pages**.
4. Under "Branch", pick `main` and folder `/ (root)` → Save.
5. Wait ~1 minute, refresh — GitHub gives you a link like:
   `https://YOUR_USERNAME.github.io/vault-store/`
   That's your live store. Share this link with users.

## 2. Add a new app

You need two things ready before editing `apps.json`:

**A) The APK's direct link**
1. In the same repo (or any repo), open the **Releases** tab → "Create a new release".
2. Give it a tag (e.g. `v1.0`), attach your `.apk` file, publish.
3. Right-click the uploaded APK on the release page → "Copy link address". That's your `apk` URL.

**B) The app icon's direct link**
- Easiest: put the icon image inside an `icons/` folder in the same repo (upload via "Add file"), then use a relative path like `icons/myapp.png`.
- Or use any free image host (imgbb.com, etc.) and paste its direct image URL.

**Then edit `apps.json`** and add a new entry to the array:

```json
{
  "name": "My New App",
  "category": "Tools",
  "icon": "icons/myapp.png",
  "apk": "https://github.com/YOUR_USERNAME/YOUR_REPO/releases/download/v1.0/myapp.apk",
  "size": "18 MB",
  "version": "1.0",
  "rating": "4.9",
  "description": "One line about what it does."
}
```

Save the file (commit directly on github.com, or via the GitHub app/HopWeb if it supports git). The site picks it up automatically on next page load — no code changes needed.

## Categories

Any category name works. These get a fixed color automatically:
`Games`, `Tools`, `Photo`, `Social`, `Productivity`, `Entertainment`.
Anything else still works, it just cycles through the accent colors.

## Notes

- Download counts shown nowhere on the page currently — each visitor's install taps are only counted in their own browser's local storage, just to keep the button state ("Installing → Installed") working. There's no shared/admin view of totals since this is a static site with no backend.
- If you want a real admin dashboard with live download totals later, that needs a backend (Firebase, like your Royal Battle admin panel) — this static version trades that off for zero cost and zero setup.
