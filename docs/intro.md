---
sidebar_position: 1
---

# Introduction

*Welcome to my first documentation site discovering **Markdown** and built with **Docusaurus**.*

This documentation details the UX (User Experience) process assessing the documentation generator Docusaurus in terms of usability, efficiency, and practicity, through the configuration of specific content needs for the project and evaluation its behavior considering the following aspects:

## Aspects to be evaluated

The evaluation involves the following aspects:

- Ease of installation.
- Difficulty setting things up.
- Issues with some dependencies.
- How much configurations were required during installation and customization.
- Presentation of **concrete examples** (config snippets, folder structures, screenshots) with a summary.
- How painful is it to **reorder or restructure** sections later?
- How to link from one doc page to another? (relative paths, special syntax, auto-resolution by title?)
- What happens when a file is renamed or moved? - do links break silently?, or does the build warn it?
- Is it possible to reference a specific heading on another page (e.g. deep-link to "Authentication" section in the Architecture page)?

**Right Sidebar**

- Is it auto-generated from headings? Which heading levels (h2 only? h2+h3?)?
- Is it configurable per-page or globally?

**Page Composition (Content)**

- Can a single rendered page be assembled from multiple markdown files? (e.g. reusable snippets, partials, shared warning boxes)
- If not natively, what workarounds exist? (MDX components, includes, etc.)
- Can we define reusable content blocks (e.g. a "prerequisites" box used across 10 pages)?

**Content Authoring Experience**

- How close is the markdown to standard/portable markdown vs. tool-specific extensions?
- Support for: code blocks with syntax highlighting (Java, XML, YAML, Gradle, shell), tabbed code blocks (e.g. Maven vs Gradle), callouts (tip, warning, danger), collapsible sections, badges/labels

Code section:

```python
print('Hello world')
```

### What you'll need

- [Node.js](https://nodejs.org/en/download/) version 20.0 or above:
  - When installing Node.js, you are recommended to check all checkboxes related to dependencies.

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest my-website classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd my-website
npm run start
```

The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
