# Verdant — Jekyll Theme

Verdant is a clean, lush green Jekyll blog theme built with [Bootstrap 5](https://getbootstrap.com/) and [Font Awesome](https://fontawesome.com/). It features a fixed sidebar for navigation, light/dark theme toggling, category and tag archives, and an in-post table of contents — everything you need to start a personal blog.

![Theme preview](assets/images/leaf2.png)

---

## Features

- 🌿 **Verdant green colour palette** — warm light mode and deep dark mode, switchable at any time
- 📋 **Sidebar navigation** — profile avatar, blog title, nav links, and social connection icons
- 🏷️ **Categories & Tags** — automatic archive pages powered by [jekyll-archives](https://github.com/jekyll/jekyll-archives)
- 📌 **Pinned post** — mark one post as pinned and it will always appear first on the home page
- 📖 **Table of Contents** — automatically generated TOC sidebar for post pages
- ⬆️ **Scroll-to-top button** — appears when you scroll down a page
- 🍔 **Responsive burger menu** — collapses the sidebar on small screens
- 🐳 **Docker Compose** — one-command local development environment (no Ruby installation required)
- 📡 **RSS feed** — built-in feed via [jekyll-feed](https://github.com/jekyll/jekyll-feed)

---

## Project Structure

```
.
├── _config.yml          # Main site configuration
├── _config_dev.yml      # Development overrides (used by Docker)
├── _data/
│   ├── navigation.yml   # Sidebar navigation links
│   └── connection.yml   # Social/connection icon links
├── _includes/           # Reusable HTML partials (sidebar, footer, etc.)
├── _layouts/            # Page layouts (default, post, category, tag)
├── _posts/              # Blog posts (organised by year)
├── _sass/               # SCSS source files
├── assets/              # Compiled CSS, JS, fonts, images
├── index.html           # Home page
├── posts.html           # All posts listing
├── categories.html      # Categories listing
├── tags.html            # Tags listing
├── about.md             # About page
├── Gemfile              # Ruby dependencies
└── docker-compose.yml   # Docker Compose configuration for local dev
```

---

## Getting Started

### Prerequisites

You need either:

- **Docker** and a container management tool such as [Docker Desktop](https://www.docker.com/products/docker-desktop/) or [Rancher Desktop](https://rancherdesktop.io/) *(recommended — no local Ruby required)*, **or**
- **Ruby ≥ 3.1** and **Bundler**

### Running locally with Docker *(recommended)*

```bash
docker compose up
```

Once the container has finished building, open your browser and navigate to:

```
http://localhost:4000/Jekyll-Theme-Verdant/
```

The site will automatically rebuild when you save a file (`--watch` is enabled).

### Running locally with Ruby/Bundler

```bash
bundle install
bundle exec jekyll serve --config _config_dev.yml
```

Then open `http://localhost:4000/Jekyll-Theme-Verdant/` in your browser.

---

## Configuration

Open `_config.yml` and update the following values for your own site:

| Key | Description |
|-----|-------------|
| `url` | The root URL of your site (e.g. `https://yourname.github.io`) |
| `baseurl` | Sub-path if your site lives at a sub-directory (e.g. `/my-blog`). Leave empty (`""`) for a root deployment. |

### Navigation links

Edit `_data/navigation.yml` to add, remove, or reorder sidebar navigation items:

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
```

### Social / connection links

Edit `_data/connection.yml` to update the icon links shown at the bottom of the sidebar. Icons use Font Awesome class names:

```yaml
- name: github
  icon: "fab fa-github"
  url: "https://github.com/your-username"
```

---

## Writing Posts

Create a new Markdown file in `_posts/` following the Jekyll naming convention:

```
_posts/YYYY/YYYY-MM-DD-post-title.md
```

### Front matter options

```yaml
---
post_title: My Post Title        # Display title (falls back to `title` if omitted)
description: A short summary.    # Shown on listing pages
categories: [Category A, How To]
tags: [Tag1, Tag2]
pinned: true                     # Optional — pins the post to the top of the home page
excerpt_separator: <!--end_excerpt-->
---
```

### Pinned post

Only the **first** pinned post (chronologically latest) is displayed on the home page. Set `pinned: true` in a post's front matter to pin it.

---

## Theming

The theme ships with a **light** and a **dark** colour scheme. Colours are defined using CSS custom properties in `_sass/themes.scss`. A JavaScript-powered toggle button (☀️/🌙) lets visitors switch between modes, and the preference is persisted in `localStorage`.

---

## Deploying to GitHub Pages

Because this theme uses `jekyll-archives`, which is not on the GitHub Pages safe allowlist, you **must** deploy via a GitHub Actions workflow rather than letting GitHub Pages build the site directly.

1. Update `url` and `baseurl` in `_config.yml` to match your GitHub Pages URL.
2. In your repository **Settings → Pages**, set the source to **GitHub Actions**.
3. Add a workflow file (e.g. `.github/workflows/deploy.yml`) that builds the site with `bundle exec jekyll build` and then uploads the `_site` directory as a Pages artifact. GitHub provides an [official starter workflow](https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml) you can use as a base.
4. Push your changes — the workflow will build and publish the site automatically on every push to your default branch.

---

## License

This theme is open source. Feel free to use and adapt it for your own blog.
