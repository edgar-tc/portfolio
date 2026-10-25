# Portfolio – Landing Page (laptop version)

A one-page personal website for a Cloud & DevOps Engineer who is looking for a new job.
This version is built for **laptop / desktop screens**. Tablet and mobile will be added later.

## How to run

No build step and no installs needed.

1. Keep the folder structure exactly as it is.
2. Double-click `index.html` to open it in Chrome, Edge, Safari or Firefox.
   (or run `python3 -m http.server` in this folder and open http://localhost:8000)

## Folder structure

```
portfolio-landing/
├── index.html          page content (text, links, images)
├── css/styles.css      all design: layout, colours, animation, hover effects
├── js/main.js          splits the name into letters for the animation
├── assets/
│   ├── photo.webp      cut-out portrait with transparent background
│   └── resume.pdf      (add this) file for the Download Resume button
└── README.md
```

## What to change (placeholders)

| What | Where |
| --- | --- |
| First / last name | `index.html` → the two `data-split` words inside `<h1 class="name">` (also the `<title>` and the photo `alt`) |
| Job title and intro text | `index.html` → `<section class="intro">` |
| Social links | `index.html` → the four `<a class="card …">` links (LinkedIn, GitHub, Instagram, mailto) |
| Resume | put your PDF at `assets/resume.pdf` |
| Photo | replace `assets/photo.webp` with another PNG/WebP that has a **transparent background** and keep the same width (720 px) |
| Colours / font | `css/styles.css` → section 1, "Design tokens" |
| Size of the big name | `--name-size` in the same section (192 fits "YOUR NAME"; reduce it for longer names) |

## How the sizing works

The mockup was designed on a 1600 px wide canvas. Sizes in the CSS look like
`calc(var(--u) * 46)`, which means "46 pixels of the mockup". `--u` is 1/1600 of the page width,
so the page scales smoothly to any laptop screen and always matches the mockup. Maximum width is 1600 px;
on wider screens the page is centred.

## Animations (on page load)

| Time | What happens |
| --- | --- |
| 0.0 – 0.7 s | Availability badge, menu and Let's Talk button slide down |
| 0.5 – 2.2 s | Name letters rise one by one |
| 1.4 – 2.7 s | Photo rises from the bottom (grows from 90% to 100%) |
| 2.3 – 3.3 s | Curved line fades in |
| 2.4 – 3.4 s | Job title, intro text, Download Resume slide up |
| 3.0 – 4.4 s | Social cards slide in from the right, one by one |
| Always | Photo floats up and down, green dot pulses, dot moves along the curved line |

## Hover effects

* **Menu links:** underline slides in from the left (250 ms).
* **Let's Talk / Download Resume:** white fill sweeps across (400 ms), button lifts 4 px, arrow nudges up-right.
* **Social cards:** black fill sweeps across (400 ms), text and icon turn white, card shifts 8 px left, arrow nudges up-right.

Animations are switched off automatically for visitors who enabled "reduce motion" on their device.

## Not included yet

* Tablet and mobile layouts.
* The other pages (Projects, Skills, Experience, Contact, Footer).
* Menu links (`#projects`, `#skills`, …) will point to the real pages once they exist.

---

## Contact page (added)

* `contact.html` + `css/contact.css` + `assets/contact-photo.webp`
* The **Contact** link in the landing page menu opens `contact.html`; the **Home** link and the
  availability badge on the contact page go back to `index.html`.
* It reuses the shared top bar, buttons and hover effects from `css/styles.css`.
* Placeholders to replace in `contact.html`: `YOUR_EMAIL@example.com` (3 places), LinkedIn handle, location.
* The handwritten note uses the Google font **Caveat**. Change `font-family` in `.c-note` to use another one.
* Laptop layout only for now. On smaller screens it keeps the laptop design and scales down until its tablet / mobile layout is built.

---

## Experience page (added)

* `experience.html` + `css/experience.css` + `js/experience.js` + `assets/experience/`
* Same structure as the LinkedIn Experience section: company header (logo, name, type, duration),
  roles on a timeline, description bullets, media cards (click a card to open the full image), and skills line.
* **Real-time durations:** the company duration and the current role ("Feb 2026 – Present") are calculated by
  `js/experience.js` from `data-start` / `data-end` (format `YYYY-MM`, `"present"` = today). Months are counted
  inclusively like LinkedIn (Oct 2025 → Oct 2026 = 1 yr 1 mo). To change a date, edit those two attributes.
* **Links:** the CGI logo / name opens https://www.cgi.com and the college logo / name opens https://sairam.edu.in/
  in a new tab.
* **Add another role:** copy one `<li class="x-role reveal"> … </li>` block inside `<ol class="x-roles">`.
* **Add another company or school:** copy a whole `<article class="x-company reveal"> … </article>` block.
* **Change an image:** replace the files in `assets/experience/` (`*-thumb.webp` = card picture, `*-full.webp` = full size).
* Laptop layout only for now (on smaller screens it keeps the laptop design and scales down).
* The Experience menu link on every page now opens `experience.html`.

---

## Skills & Tools page (added)

* `skills.html` + `css/skills.css` + `js/skills.js` + `assets/skills/` (logos as SVG files)
* 12 tool cards in a 6-column grid (AWS, Terraform, Docker, Kubernetes, Jenkins, ArgoCD, CloudFormation, Linux,
  Python, Git, Prometheus, Grafana) plus a dark **Agentic AI** feature card underneath.
* **Add or remove a tool:** copy or delete one `<li class="s-tool reveal">` block in `skills.html`
  (put the logo in `assets/skills/`). The `--i` number controls the order of the entrance animation.
* **Agentic AI text and chips:** `<section class="s-ai …">` in `skills.html`.
* Logos: most are from the open-source Devicon set (MIT licence). `cloudformation.svg` and `agentic-ai.svg` are simple custom icons.
  Replace any file in `assets/skills/` with an official logo if you prefer.
* Hover: cards lift and the logo grows; the Agentic AI chips turn white. Cards fade in one after another on scroll.
* The Skills menu link on every page now opens `skills.html`.
* Laptop layout only for now.

---

## Projects pages (added)

* `projects.html` – overview: heading, filter buttons, and one card per project (title, short summary, tags, arrow).
  Cards are grouped into **Personal Projects** and **Office Projects (CGI)**.
* `project-*.html` – one full page per project (7 pages). Each has a **Back to Projects** button at the top,
  the title, the full context on the left (overview, highlights, numbered key contributions), a sidebar on the right
  (picture, tech stack, details) and previous / next project buttons at the bottom.
* `css/projects.css` and `js/projects.js` are shared by all eight pages.
* **Filters:** each card has `data-filters="aws monitoring …"`. The button `data-filter="aws"` shows the cards that contain it.
* **Add a project:** (1) copy one `<li class="p-card …">` block in `projects.html` and edit it, (2) copy a `project-*.html`
  page and edit its text, (3) point the card's link to the new page.
* **Banner pictures** are built from tool logos (`assets/skills/`) and a few small icons (`assets/projects/`);
  change the logos inside the `<div class="p-banner …">` block.
* Replace `YOUR_GITHUB_USERNAME` in the **View GitHub** button of `projects.html`.
* The Projects menu link on every page now opens `projects.html`. Laptop layout only for now.

---

## About page (added)

* `about.html` + `css/about.css` + `js/about.js` + `assets/about/profile.webp`
* Sections: intro with photo and quick-facts cards, "More about me" text, four value cards,
  "My Journey" timeline, and "Interests & Hobbies".
* **Edit the text** directly in `about.html`. **Hobbies:** edit the `<li>` items in `<ul class="a-hobbies__grid">`
  (icons are defined at the top of the file, e.g. `#i-gym`, `#i-chart`).
* **Timeline:** each `<li>` inside `<ol class="a-timeline">` is one point; the page is built for 3 points
  (if you add or remove points, change `repeat(3, 1fr)` and `100% / 3` in `.a-timeline` in `css/about.css`).
* **Resume:** the Download Resume button expects `assets/resume.pdf` (add your file).
* **Email:** replace `yourmail@example.com` (info card).
* **Education card:** currently "Bachelor's Degree"; write the exact degree name if you want it shown.
* The **About** link was added to the menu of every page, and the **About Me!** button on the landing page opens this page.
* Laptop layout only for now.
