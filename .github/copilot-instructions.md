This repository is a small static site (GitHub Pages-style) serving a Vietnamese-focused content hub for Dalatmilk products.

Quick orientation
- Site is plain HTML files at the repo root and under `posts/` and `en/posts/`. Example posts: `posts/bi-quyet-pha-ca-phe-kem-muoi.html`, `en/posts/secret-to-making-salted-cream-coffee.html`.
- Primary assets are referenced by absolute URLs (e.g. `https://dalatmilkdanang.github.io/images/post01-cover.jpg`). The site uses Tailwind via CDN (see `script src="https://cdn.tailwindcss.com"` in heads).
- Important site files: `index.html`, `sitemap.xml`, `robots.txt`, `README.md`.

What to do when editing content
- Prefer editing the HTML files in `posts/` or `en/posts/` directly. Maintain existing meta tags (title, description, keywords, canonical) and keep `link rel="alternate" hreflang` pairs when updating localized content.
- Preserve existing Open Graph (`og:*`) and JSON-LD (`application/ld+json`) blocks; update `og:image` and `image` URLs to point to the image served under the repo (or an absolute CDN URL).
- Keep the `canonical` and `hreflang` values in sync between `posts/` and `en/posts/` for parallel translations.

Patterns and conventions to follow
- Static HTML pattern: each article page has a head with meta + OG + Twitter + JSON-LD, then a body with a simple Tailwind-based layout (navbar, main article, footer). Mirror this pattern when adding new posts.
- Images in posts commonly use full absolute URLs and currently may be placeholders (e.g., `placehold.co`). When adding product/feature images, add descriptive `alt` attributes and `loading="lazy"` to img tags.
- Links to commercial pages use an external `dalatmilkshop.com` URL for ordering; preserve `rel="noopener noreferrer" target="_blank"` on these links.

Build & deploy notes (discoverable from repo layout)
- This repo is structured for static hosting (GitHub Pages). No build step is present in the repository. Assume edits are deployed by pushing to the `main` branch.
- If committing a change that modifies `sitemap.xml` or `robots.txt`, update those files manually; there is no generator in repo.

When automating or adding tooling
- If you introduce a build pipeline (e.g., GitHub Actions), keep the output as static HTML files at repository root so GitHub Pages behavior remains unchanged.
- Adding image optimization, RSS generation, or minification is fine — include a small README section explaining any new dev workflow (build commands) and update `README.md`.

Examples from this repo (use these to infer intent)
- `posts/bi-quyet-pha-ca-phe-kem-muoi.html`: canonical/hreflang pairing with `en/posts/secret-to-making-salted-cream-coffee.html`, contains OG/Twitter and JSON-LD blocks — follow this head structure.
- `index.html`: lightweight landing page with same header/footer pattern — reuse CSS rules and Tailwind CDN approach.

Safety and non-goals
- Do not attempt to refactor the site into a dynamic framework without an explicit issue/approval. Keep changes minimal and predictable.
- Avoid changing external commercial links or phone numbers unless instructed.

If unsure, follow these steps
1. Open the target HTML file in `posts/` or `en/posts/`.
2. Match the head structure (title, meta description, canonical, alternate/hreflang, OG, Twitter, JSON-LD).
3. Add `alt` and `loading="lazy"` to images and preserve Tailwind classes.
4. Update `sitemap.xml` manually if adding/removing pages and mention it in the commit message.

Ask questions when any of these are true
- You need to change deployment behavior (introduce a build step, CI, or change branch). Provide a short plan.
- You want to convert HTML posts to a generator (Jekyll/Hugo) — propose a migration plan and a small proof-of-concept.

If you update this instruction file, keep it concise and cite a small example file (one or two filenames) demonstrating the pattern.
