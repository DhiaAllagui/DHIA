# DHIA

Personal portfolio site for Dhia — Creative Developer & Digital Designer. A single-page site covering graphic design, video editing, web development, and mobile experiences.

## Sections

- **Hero** — intro headline and quick actions
- **About** — short statement
- **Services** — Graphic Design, Video Editing, Web Development, Mobile Development
- **Selected Work** — filterable project grid (Design / Video / Web / Mobile)
- **Featured Project** — highlighted case study
- **Toolbox** — tools & technologies (dev, design, video)
- **About Me** — background and stats
- **Contact** — email, GitHub, LinkedIn

## Stack

Single static file — plain HTML, CSS, and vanilla JavaScript. No build step, no dependencies.

## Running locally

Just open [index.html](index.html) in a browser, or serve it:

```bash
npx serve .
```

## Repository layout

```
index.html
assets/
  images/
    graphic-design/
    web/
    mobile/
    branding/
  videos/
  documents/        (e.g. Dhia-CV.pdf)
projects/
  <project-name>/
    index.html      (a fully static sub-project, hosted at /projects/<project-name>/)
```

## Adding a project

Projects live in the `projects` array near the top of the `<script>` block in [index.html](index.html) — edit that array only, no other HTML changes needed. Each entry:

| Field | Description |
|---|---|
| `title`, `category`, `description` | Shown on the card and in the modal |
| `type` | `design`, `video`, `web`, or `mobile` — drives the filter buttons |
| `hosting` | `static` (real live URL), `case-study` (no hosting, opens a detail modal), or `github-only` (links straight to the repo) |
| `technologies` | Array of tag strings |
| `image` | Path to a real thumbnail. Leave `''` to keep the current placeholder mockup |
| `gallery` | Array of extra screenshot paths shown in the modal |
| `video` | Path to a video file, shown as a native player in the modal |
| `liveUrl` | Only set this if the project is genuinely hosted somewhere (e.g. `projects/athleo/` or an external domain) |
| `githubUrl` | Only set this if you have a real repository link |
| `contribution` | Array of bullet points describing your role, shown in the modal |

**Images** → drop them in the matching `assets/images/<category>/` folder and reference them as `assets/images/web/athleo-01.jpg`.

**Videos** → `assets/videos/`, referenced the same way.

**Static website projects** (plain HTML/CSS/JS) → place the whole project under `projects/<name>/index.html`, then set `liveUrl: "projects/<name>/"` and `hosting: "static"`. GitHub Pages serves it directly at `https://USERNAME.github.io/projects/<name>/`.

**Backend projects** (PHP, Symfony, MySQL, Node, Java/Android, or anything needing a server) — GitHub Pages cannot run these. Leave `liveUrl` empty and `hosting: "case-study"`; the card opens a project modal with description, contribution, tech stack, screenshots, and a GitHub link instead of a broken demo.

**No GitHub repo yet** → leave `githubUrl` empty; the modal simply omits that button rather than linking somewhere fake.

## Deploying

Live at https://dhiaallagui.github.io/DHIA/. Sub-projects under `projects/<name>/` are served automatically at `/projects/<name>/` once Pages is enabled — no extra configuration needed.
