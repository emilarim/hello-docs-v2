---
sidebar_position: 1
---

# Installation Considerations

The installation of the documentation generator can be done following the installation recommendation provided by the owners on **[docusaurus.io](https://docusaurus.io)**.

- It provides the requisites to install and a guide with simple number of steps to follow in order to deploy a scaffold project website with a structure rundown.
- It requires installation of `Node.js` to run the official scaffold commands to create a Docusaurus project, start the development server, create documentation page, build the static website, and configure Docusaurus for GitHub pages.
- Installation of `git` requires to initialize Git, connect to GitHub, and host the Docusaurus site in it.
- Docusaurus supports *Hot reload*, so only saving the project, the website is uploading.

### Difficulties Encountered

- Identify and be familiarized with the website features configured in the document structure´s left side panel requires time (e.i., docusaurus.config.js), in order to add, edit or delete parameters.

For example, using the correct folder to reference images (`static` folder) to avoid compiled issues:

![CompiledIssues](/img/CompiledIssues.png)

- To implement a documentation structure, it may require to configure manually a folder structure inside `docs/`, `sidebars.js` as chapters, and Markdown pages `.md`. 

Basic Project Layout Deployed:
```
hello-docs/
  ├── .docusaurus/
  ├── blog/
  ├── build/
  └── docs/
  ├── node_modules/
  ├── src/
  ├── static/
  |
  ├── docusaurus.config.js
  ├── package-lock.json
  ├── package.json
  ├── README.md
  └── sidebars.js
```

- Sidebar management brings problems such as keeping sidebar order consistency, linking sidebar items to correct files, and maintaining large `sidebars.js`.

## GitHub Configuration

In order to host the full website converted in GitHub, it is necessary to create a repository on GitHub, configure the `docusaurus.config.js` for GitHub pages, 

### Difficulties Encountered
- Docusaurus requires a full URL with `https://` in the `url` field:

![IncorrectSyntax](/img/IncorrectSyntax.png)

- Wrong configuration of `url` or `baseUrl`:

![WrongRepository](/img/WrongRepository.png)

- Authentication errors:

![InvalidAuth](/img/InvalidAuth.png)


The website is hosted and available at [https://github.com/emilarim/hello-docs](https://github.com/emilarim/hello-docs).
