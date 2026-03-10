---
sidebar_position: 2
---

# Testing Configurations

Documents are **groups of pages** connected through:

- a **sidebar**
- **previous/next navigation**
- **versioning**

## Creating a Mermaid Diagram

1. Enabling the oficial Mermaid theme

```js title="docusaurus.config.js"
const config = {
  title: 'Hello Docs',
//new config
  markdown: {
    mermaid: true,
  },

  themes: ['@docusaurus/theme-mermaid'],
};
```

2. Installing the Theme

```bash
npm install @docusaurus/theme-mermaid

```

Here is a simple flowchart:

```mermaid
graph TD
A-->B

```


pie title Documentation Content Types
    "Tutorials" : 40
    "API Reference" : 30
    "Examples" : 20
    "Guides" : 10

User->>Docusaurus: Writes documentation;
    Docusaurus->>Mermaid: Renders diagram;
    Mermaid-->>User: Displays beautiful chart;

A new document is now available at [http://localhost:3000/docs/hello](http://localhost:3000/docs/hello).

## Security Concerns

After installing the package `@docusaurus/theme-mermaid` in the Node.js /npm ecosystem, 19 high severity vulnerabilities were reported that usually comes from dependencies of dependencies.

![vulnerabilitiesReported](/img/VulnerabilitiesReported.png)


Running the `npm audit` command to identify dependencies with vulnerabilities:

![vulnerabilityReport](/img/VulnReport.png)

> **[Download the detailed log](/logs/npmAuditReport.txt)**

### Analyzing Security Vulnerabilities

 Based on the NPM Audit Vulnerability Report: 

#### Root Vulnerability

| Severity | Package | Version | Issue | Fix Available |
|----------|---------|---------|-------|---------------|
| High | serialize-javascript | ≤ 7.0.2 | RCE via RegExp.flags and Date.prototype.toISOString() | `npm audit fix --force` |

#### Dependency Chain Impact

| Direct Package | Vulnerable Version | Depends On | Current Status |
|----------------|-------------------|------------|----------------|
| copy-webpack-plugin | 4.3.0 - 13.0.1 | serialize-javascript | Vulnerable |
| css-minimizer-webpack-plugin | ≤ 7.0.4 | serialize-javascript | Vulnerable |

#### Affected Docusaurus Packages

| Package | Affected Versions | Notes |
|---------|-------------------|-------|
| **@docusaurus/bundler** | All versions | Depends on vulnerable copy-webpack-plugin and css-minimizer-webpack-plugin |

#### Packages Dependent on @docusaurus/core

| Package | Affected Versions | Dependencies |
|---------|-------------------|--------------|
| @docusaurus/core | ≤0.0.0-6119, 3.5.2-canary-6121 - 3.5.2-canary-6131, ≥3.6.0-canary-6132 | Depends on @docusaurus/bundler |

#### Core Plugins Affected

| Plugin Category | Package Name | Affected Versions |
|-----------------|--------------|-------------------|
| **Content Plugins** | @docusaurus/plugin-content-blog | ≤0.0.0-6119, 3.5.2-canary-6121 - 3.5.2-canary-6131, ≥3.6.0-canary-6132 |
| | @docusaurus/plugin-content-docs | Same as above |
| | @docusaurus/plugin-content-pages | Same as above |
| **Theme Plugins** | @docusaurus/theme-classic | Same as above |
| | @docusaurus/theme-mermaid | Same as above |
| | @docusaurus/theme-search-algolia | Same as above |
| **SEO & Analytics** | @docusaurus/plugin-google-analytics | Same as above |
| | @docusaurus/plugin-google-gtag | Same as above |
| | @docusaurus/plugin-google-tag-manager | Same as above |
| | @docusaurus/plugin-sitemap | Same as above |
| **Utility Plugins** | @docusaurus/plugin-debug | Same as above |
| | @docusaurus/plugin-css-cascade-layers | Same as above |
| | @docusaurus/plugin-svgr | Same as above |

#### Preset Package

| Package | Affected Versions | Dependencies |
|---------|-------------------|--------------|
| @docusaurus/preset-classic | ≤0.0.0-6119, 3.5.2-canary-6121 - 3.5.2-canary-6131, ≥3.6.0-canary-6132 | Depends on all core and content plugins listed above |

#### Summary Impact

| Metric | Count |
|--------|-------|
| **Total Vulnerabilities** | 19 (High severity) |
| **Root Vulnerable Package** | 1 (serialize-javascript) |
| **Direct Dependencies Affected** | 2 (copy-webpack-plugin, css-minimizer-webpack-plugin) |
| **Docusaurus Packages Affected** | 15+ |
| **Breaking Change Required** | Yes (will install @docusaurus/core@3.5.2) |

### Recommended Action

1. Try to fix first:

Running the `npm audit fix` in order to update *only compatible dependency versions*, respect the *version ranges defined in `package.json`*, avoid *breaking changes*, and install *minor or patch updates only*.

![npm audit-fix](/img/npmAuditFix.png)

2. As the vulnerabilities remain, the next step consisted of updating Docusaurus Core:

![Updating Docusaurus Core](/img/UpdatingDocusaurusCore.png)

3. Last resort (may include breaking changes):
Running the `npm audit fix --force` in order to allows *major upgrades*, and modify the dependency tree *drastically*.



