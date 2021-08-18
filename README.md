**At the moment this is just hosting some test pages but they may be useful for some people in any case. A more robust/complete set of notes/articles will be uploaded in due course***

<br>

# Dante's Obsidian-Based GitHub Pages Repo

Using [this](https://github.com/jobindj/obsidian-mkdocs) pre-configured MkDocs-based template as the basis for our site. However this was only to get started, the site could genuinely be configured manually in a very short time. There are a lot of resources online to help. 

Have customised the configuration significantly following the notes on the [Material theme](https://squidfunk.github.io/mkdocs-material/setup/changing-the-colors/).

Also we don't actually need an Obsidian-specific template since we're using the Obsidian [Consistent Attachments And Links](https://github.com/derwish-pro/obsidian-consistent-attachments-and-links) plugin to ensure that notes are using Markdown formatting which is recognised wider than just Obsidian. 
The only Obsidian-specific thing I can tell about the template is that it supports 'roam' style links.

Make sure to select the 'gh-pages' branch as the source of the Pages in settings - this branch is created by GitHub Actions when any changes are pushed. The action workflow is defined in `/.github/workflows/ci.yml`.
Displayed pages go in the `/docs` directory. And a menu is generated based on the flder structure used. 
