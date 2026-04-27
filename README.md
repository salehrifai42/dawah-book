# Everyone is a Daee — Bilingual Book Site

A single-page bilingual website with an English ⇄ Urdu language toggle.

## Files

- **`index.html`** — the entire site (HTML, CSS, JS in one file)
- **`content.js`** — the book content (both languages)

That's it. Two files. No build step, no dependencies, no server-side code.

## How to test locally

Open a terminal in this folder and run:

```
python3 -m http.server 8000
```

Then open <http://localhost:8000> in your browser.

(You can't just double-click `index.html` because browsers block scripts loading local files via `file://`. The local server fixes that.)

## Deployment — pick one (all free)

### Option 1: GitHub Pages (recommended for a permanent home)

1. Create a free GitHub account if you don't have one.
2. Create a new public repository, e.g. `dawah-book`.
3. Upload `index.html` and `content.js` into the repository (drag-and-drop on github.com works).
4. In the repo, go to **Settings → Pages**.
5. Under "Source", select **Deploy from a branch**, choose `main` and `/ (root)`, then Save.
6. Wait ~1 minute. Your site will be live at `https://YOUR-USERNAME.github.io/dawah-book/`.

To use a custom domain later (e.g. `dawahbook.com`), add a `CNAME` file with the domain and configure DNS. Free.

### Option 2: Cloudflare Pages (fastest, best CDN)

1. Sign up at <https://pages.cloudflare.com> (free).
2. Click "Upload assets" — drag the folder containing `index.html` and `content.js`.
3. Pick a project name. It deploys instantly to `https://YOUR-PROJECT.pages.dev`.
4. Custom domain is free if you move DNS to Cloudflare.

### Option 3: Netlify drop (zero account needed to start)

1. Go to <https://app.netlify.com/drop>.
2. Drag the folder onto the page.
3. You get a live URL in seconds. Sign up to keep it permanent.

### Option 4: Vercel

Same as Cloudflare Pages — drag and drop, instant deploy. Sign up at <https://vercel.com>.

## Editing the book

To update the text, edit the source `.docx` files (or markdown), regenerate, and replace `content.js`. The structure of `content.js` is just:

```js
window.__BOOK_CONTENT__ = {
  "en": "# heading\n\nparagraph...",
  "ur": "# سرخی\n\nپیراگراف..."
};
```

You can edit it directly in any text editor if needed. The renderer supports:

- `# ` and `## ` headings
- `**bold**` and `*italic*`
- Pure-Arabic-script lines automatically render as centered ayah
- Italic-quoted lines automatically render as gold-bordered quote blocks

## What it does

- **Single-page book** — the entire content lives on one URL, fast to load (~70 KB total).
- **Language toggle** — sticky header with EN / اردو buttons. Sliding pill animation.
- **Persisted preference** — remembers your last language choice via localStorage.
- **Proper RTL** — when Urdu is active, the article flows right-to-left with Noto Nastaliq Urdu font.
- **Responsive** — clean on mobile, brand bar hidden to keep things minimal.
- **No tracking, no cookies, no JS frameworks**, no build step. Pure HTML/CSS/JS.
- **Accessible** — semantic HTML, `aria-selected` on the toggle, `prefers-reduced-motion` honored.

## Custom domain (optional, for later)

A `.com` is around $10/yr from Namecheap, Cloudflare Registrar, or Porkbun. Cloudflare Registrar sells at cost (no markup). Once you own the domain, all four hosts above let you attach it for free.
