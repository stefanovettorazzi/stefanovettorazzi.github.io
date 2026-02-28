# GitHub Copilot Instructions

When assisting with this repository, adhere to the following rules:

1. **Preserve User Data Values:** The embedded `<script id="site-data" type="application/json">` inside `index.html` contains the user's actual live data (song releases, social links, artwork URLs). If you need to modify the *structure* of this JSON for a feature request, **you must preserve all existing data values exactly as they are**. Do NOT overwrite or reset the values with placeholders unless explicitly confirmed by the user.
2. When making layout or Javascript changes that do not require structural data changes, preserve the existing JSON block exactly as the user left it.
3. The site language is strictly Spanish (`es-UY`).
4. Keep the design simple and adhere to the single-page application structure.
5. **Adding New Releases:** When the user provides URLs (like Apple Music or Spotify) for a new release, automatically assume the following workflow:
   - Run a terminal command (e.g., `curl -sL <URL> | grep 'og:image'`) to fetch the artwork URL from the `<meta property="og:image">` tags of the provided link.
   - Download that image directly into an `images/` folder in the repository using the terminal (e.g., `curl -o images/new-song-cover.jpg <IMAGE_URL>`).
   - Prefix the new release item to the top of the `"releases"` array in the `index.html` JSON block, updating the `"artwork"` property to reference the local relative path (e.g., `images/new-song-cover.jpg`).
   - Manage the `"id"` fields correctly (the newest should be `"release-latest"`, shift older ones to `"release-2"`, `"release-3"`, etc.).