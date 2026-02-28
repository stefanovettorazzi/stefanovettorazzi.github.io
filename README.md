# Stefano Vettorazzi - Artist Website

This is the repository for my personal artist website. The site is a single-page application built with HTML, CSS, and Vanilla JavaScript. 

## How to Add a New Release

To add a new song or album to the website, follow these simple steps to ensure it shows up at the top:

### 1. Add the Artwork
- Place your new cover art image into the `images/` directory. (It can be a `.jpg`, `.jpeg`, or `.png`).
- **Important Note:** There is an automated GitHub Action set up on this repository. Whenever you push a new image, the Action will automatically convert it to a highly-optimized `.webp` format and delete the original file. 

### 2. Update the Website Data
- Open `index.html` and scroll down to find the `<script id="site-data" type="application/json">` block.
- Inside the `"releases"` array, paste a new item at the **very top** of the list.

### 3. Data Format
Use the following format for your new release. **Make sure to use the `.webp` extension** in the `"artwork"` path to match the file that the GitHub Action will generate.

```json
{
    "title": "Your New Song Title",
    "artwork": "images/your_new_song_image_name.webp",
    "links": {
        "spotify": "https://open.spotify.com/...",
        "apple": "https://music.apple.com/...",
        "youtube": "https://www.youtube.com/..."
    }
},
```
*(Don't forget the comma `,` at the end of the curly brace to separate it from the older release below).*

### 4. Commit and Push
Once your image is in the `images/` folder and `index.html` is updated:
1. Stage your changes: `git add .`
2. Commit: `git commit -m "content: add new release [Song Title]"`
3. Push: `git push`

The GitHub Action will handle converting your image to `.webp`, and your live site will update automatically featuring the new release at the top!

---

## How to Update Social Links
To update your social links (Instagram, TikTok, X, YouTube), simply modify the URLs under the `"artist": { "socials": { ... } }` object at the top of the JSON data inside `index.html`.
