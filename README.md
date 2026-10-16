# Abinandan Pradeep | Cybersecurity Portfolio

A static personal portfolio for an entry-level cybersecurity candidate. It is plain HTML, CSS and JavaScript, so it needs no build step and no backend and can be hosted directly on GitHub Pages.

## Overview

The site presents my skills, projects, credentials and contact details honestly for an entry-level profile. Content that is not yet confirmed (credential status, CV, repository links) is clearly marked or hidden until real information is added.

## Features

- Dark hero with light content sections, plus a dark/light theme toggle that remembers your choice (falls back to your system preference on the first visit)
- Sticky responsive navigation with a mobile menu, active-section highlighting and keyboard support
- Skills grouped by area, with no fake proficiency scores
- Project cards rendered from a data array, with working category filters
- Certification cards with an editable status and optional credential link
- Education, practical learning, GitHub and contact sections
- Profile photo with an "AP" initials fallback
- CV download button that only works when the PDF exists
- Reveal-on-scroll animations that respect `prefers-reduced-motion`
- Skip link, visible focus styles and semantic landmarks

## Technology stack

HTML5, CSS3 (custom properties, Flexbox, Grid) and vanilla JavaScript. Optional external resources: Google Fonts, Devicon (four skill icons via jsDelivr) and the ghchart.rshah.org contribution graph. The site works if any of these fail to load.

## Repository structure

```text
abhinandan-portfolio/
├── index.html
├── README.md
├── css/
│   └── style.css
├── js/
│   └── script.js
└── assets/
    ├── images/
    │   └── profile.jpg            (you add this)
    ├── icons/
    │   └── favicon.svg
    └── Abinandan_Pradeep_CV.pdf   (you add this)
```

## Local preview

Open `index.html` in a browser, or run a small local server from the project folder:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`. Opening the file directly works too, but a server behaves more like GitHub Pages.

## Deploy to GitHub Pages

1. Sign in to GitHub and click **New repository**.
2. Choose a name. Use `abhinandu0712-cyber.github.io` for a **user site** published at `https://abhinandu0712-cyber.github.io/`. Any other name (for example `portfolio`) makes a **project site** at `https://abhinandu0712-cyber.github.io/portfolio/`.
3. Set the repository to **Public** and create it.
4. Click **uploading an existing file**, drag in everything inside the `abhinandan-portfolio` folder (keep the `css`, `js` and `assets` folders), and click **Commit changes**. `index.html` must be at the top level of the repository.
5. Open the repository **Settings**, then **Pages**.
6. Under **Build and deployment**, set Source to **Deploy from a branch**, choose branch `main` and folder `/ (root)`, then **Save**.
7. Wait one to two minutes and refresh the Pages settings. The published URL appears at the top.
8. Test it on your computer and on your phone.

All links in the site are relative (for example `css/style.css`), so they work for both user sites and project sites. If you create a project site, update the `og:url` and `og:image` addresses in `index.html` to include the repository name.

To update the site later, edit a file on GitHub (pencil icon) or upload the changed file again, then commit. Pages republishes automatically.

## Replace the profile photo

Save a portrait (roughly 800 x 1000 px, JPG) as `assets/images/profile.jpg`. Until then the initials "AP" are shown.

## Add or replace the CV

Place your PDF at `assets/Abinandan_Pradeep_CV.pdf`. Until the file exists, the button shows a short "not uploaded yet" message instead of a broken download. The check runs when the site is served over http or https; it is skipped when opening the file directly from disk. To use another filename, change `cvPath` in `js/script.js` and the `href` of `#cv-button` in `index.html`.

## Edit skills

Skills are plain list items in the Skills section of `index.html`. Copy or remove an `<li class="skill">` block. A tile uses either a Devicon `<img>` or a short text monogram.

## Update certification statuses

In `js/script.js`, edit the `CERTIFICATIONS` array. Set `status` to `'completed'`, `'in-progress'` or `'verify'`, and add a real credential URL in `link` when you have one. All four start as "To verify".

## Add new project cards

In `js/script.js`, add an object to the `PROJECTS` array with `title`, `category` (one of Security Tools, Blue Team, Penetration Testing), `status`, `description`, `tags`, `repoUrl` and `demoUrl`. Leave `repoUrl` or `demoUrl` empty to hide that button. Add your SentinelPass repository URL to `repoUrl` once it is published. Filter buttons update their counts automatically, and categories with no projects are disabled.

## Update social links and contact details

Search `index.html` for `linkedin.com`, `github.com` and `abhinandu0712@gmail.com` and edit each occurrence (hero, GitHub, contact and footer sections).

## Optional external widgets

- **GitHub contribution graph:** loaded as an image from `ghchart.rshah.org`. If it fails, a link to your profile is shown. To remove it, delete the `.github__graph` block in `index.html`.
- **Skill icons:** four icons come from Devicon via jsDelivr; if they fail, a text monogram is used.
- **Fonts:** Google Fonts; system fonts are used if unavailable.

No tokens, API keys or tracking are used.

## Metadata to update after deployment

In `index.html`: `og:url`, `og:image` (add a 1200 x 630 image at `assets/images/og-image.png` if you want a share preview) and the `<meta name="description">` if your focus changes.

## Known limitations and troubleshooting

- **Broken images or styles:** check that file names match exactly, including capitalisation (`profile.jpg`, not `Profile.JPG`), and that folders were uploaded.
- **Page shows a 404:** make sure `index.html` is at the root of the repository and Pages is set to `main` and `/ (root)`.
- **Changes do not appear:** wait a minute and hard refresh (Ctrl+Shift+R).
- **Projects or certifications missing:** open the browser console (F12) and look for a JavaScript error; a missing comma in the data arrays is the usual cause.
- **No contact form:** this is a static site, so there is deliberately none. Use the email link.
