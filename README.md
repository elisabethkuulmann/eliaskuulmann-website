# Elias Kuulmann — Portfolio Website

## Project Structure

```
site/
├── index.html        ← Home page (works gallery)
├── about.html        ← Artist statement
├── cv.html           ← Curriculum vitae
├── contact.html      ← Postcard-style contact form
├── style.css         ← All styles
├── script.js         ← Gallery + lightbox logic
├── images/           ← Put artwork images here
│   └── placeholder.jpg
└── fonts/            ← Put custom handwriting font here (optional)
    └── elias-hand.woff2
```

## Quick Start

1. Open `index.html` in your browser — that's it, no build step needed.
2. For local development with live reload, you can use VS Code's "Live Server" extension.

## Customisation Checklist

### 1. Replace the handwriting font
The site currently uses **Caveat** from Google Fonts as a placeholder.
To use Elias's actual handwriting:
- Create a font at [calligraphr.com](https://www.calligraphr.com/) — it's free for basic use
- Export as `.woff2` and place in `fonts/` folder
- In `style.css`, uncomment the `@font-face` block near the top
- Change `--font-hand: 'Caveat'` to `--font-hand: 'EliasHand'`

### 2. Add artwork images
- Place images in the `images/` folder
- Open `script.js` and update the `galleryData` object
- Replace `images/placeholder.jpg` with actual file paths
- Update titles and captions

### 3. Add the postcard background (optional)
If you have a scanned postcard image:
- Save it as `images/postcard-bg.jpg`
- In `style.css`, find `.postcard` and add:
  ```css
  background-image: url('images/postcard-bg.jpg');
  background-size: cover;
  ```
- You may want to reduce the opacity of form fields or adjust colours to work with the scan

### 4. Set up the contact form
Choose one of these free options:

**Option A: Formspree (easiest)**
1. Sign up at [formspree.io](https://formspree.io/)
2. Create a form and get your form ID
3. In `contact.html`, replace the TODO comment with:
   ```js
   fetch('https://formspree.io/f/YOUR_FORM_ID', {
     method: 'POST',
     headers: { 'Content-Type': 'application/json' },
     body: JSON.stringify({ email: email.value, topic: topic.value, message: message.value })
   }).then(() => {
     document.querySelector('.postcard').style.display = 'none';
     document.querySelector('.postcard-title').style.display = 'none';
     document.getElementById('confirmation').style.display = 'flex';
   });
   ```

**Option B: Netlify Forms (if hosting on Netlify)**
- Add `netlify` attribute to a wrapping `<form>` tag — Netlify detects it automatically

### 5. Fill in content
- `about.html` — Replace placeholder text with artist statement
- `cv.html` — Replace placeholder entries with real CV data
- `script.js` — Update work titles in `galleryData`
- `index.html` — Update work titles in the sidebar links

### 6. Video works
For video works, you have two options:
- **Thumbnail + link**: Show a still image that opens Vimeo/YouTube in a new tab
- **Embedded player**: Replace the lightbox image with an iframe embed

## Hosting (Free)

**Netlify:**
1. Go to [netlify.com](https://www.netlify.com/)
2. Drag and drop the `site/` folder onto the dashboard
3. Done — you get a URL like `elias-kuulmann.netlify.app`
4. Add a custom domain ($10–15/year from Namecheap or similar)

**Vercel:**
1. Go to [vercel.com](https://vercel.com/)
2. Import the project
3. Same deal — free hosting, custom domain optional

## Colours
All colours are CSS variables in `style.css` — easy to change:
- `--color-bg`: Page background (currently warm off-white)
- `--color-text`: Main text colour
- `--color-postcard`: Postcard background
- Adjust these to match Elias's aesthetic preference
