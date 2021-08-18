---
Created:  '2021-08-15 15:29:49 +01:00'
Modified: '2021-08-15 15:29:49 +01:00'
---

| Tags: #obsidian #github #github-pages #mkdocs |
| ----- |

---

> # Key Takeaways / Things to Remember
> 

---
# Publishing Obsidian Markdown Files in Github Pages

Another option is just to manually setup and configure your `mkdocs.yml` file and push the content to GitHub.

There are also various docker images for mkdocs, their purpose seems to generally be to publish the static files locally (e.g. for dev/testing) instead of having to push to GitHub first. They may be useful as sources of config data as they seem to generate config files on first run.


## Using an [MkDocs template](https://github.com/jobindj/obsidian-mkdocs)
MkDocs is simply a defined configuration and file structure that GitHub recognises and can use to display websites. 
MkDocs is a fast, simple static site generator (incl [theming](https://mkdocs.readthedocs.io/en/latest/user-guide/styling-your-docs/)) that's geared towards building project documentation. Documentation source files are written in Markdown, and configured with a single YAML configuration file. It is [supported out of the box by RTD](https://mkdocs.readthedocs.io/en/stable/), and can also host the files locally for dev purposes.

Someone has made a specific template for MkDocs to work well with Obsidian notes. See:
https://github.com/jobindj/obsidian-mkdocs
* Copy the repo template to our account (using hyperlink inside source repo). 
	
	Save in the special [danteali.github.io](https://github.com/danteali/danteali.github.io) repo which is used to publish the associated Pages at:
	https://danteali.github.io/
	
	I believe that you can generate Pages for any repo. Only the above 'special' one will be accessible at the root URL. But if using other repos, after turning on Pages options in settings, they should be published to: `<username>.github.io/<repository>`.
* Cloned repo to a working dir, e.g. `C:\Scratchpad\GitHubRepos`:
	```bash
	git clone https://github.com/danteali/danteali.github.io
	```
* Use working dir as a new Obsidian Vault: `GitHub Pages` - select the option to use existing Vault (copy main Vault's `.obsidian` directory to retain settings etc)
* Place any markdown files in the docs folder. Any subfolders will be treated as 'groups' in the generated table of contents on the site.
* Even though we have a `README.md` in the root of the repo, the deployed Pages will start in the `docs` folder
* Push changes to github:
	```bash
	cd <working dir>
	git add .  
	git commit -m "Update"  
	git push origin main
	```
	- The `push` command uses `origin` to indicate the default remote repository name, and the last argument should specify the destination branch name. In this case the template we copied uses `main` as the repo branch name.
		We can push to any branch name we choose (e.g. if we want to retain a version for rollback later) - github will process the branches named in the `ci.yml` workflow file below.
* When changes are pushed to GitHub, Actions are triggered as defined in the `../.github/workflows/ci.yml` file.
	These process the `mkdocs.yml` configuration and interpret the repo content in line with this. 
	A new branch is created/updated by the Actions. This is called `gh-pages`.
* In GitHub repo Settings -> Pages make sure to select the `gh-pages` branch.

* If there are any changes in the online GitHub repo which are not reflected in the local working dir (e.g. cloned to NAS instead of desktop and made some changes), we can update the local repo by 're-cloning' or we can `pull` those changes to the local repo:
	```bash
	git pull origin main
	```
	* Again, in `pull` command we need to specify the remote branch name to pull to the local working dir.
	* In fact, Git prevents you from overwriting the central repository’s by refusing to push requests when they result in a non-fast-forward merge. So, if the remote history has diverged from your history, you need to pull the remote branch and merge it into your local one, then try pushing again.
		Or you can use the `git push --force` option to force a merge even if the local repo is not consistent with the remote one.

* The `mkdocs.yml` file can be amended to further configure the site's theme, colours, etc.
	See: 
	* https://www.mkdocs.org/
	* Customising Material theme:
		* https://squidfunk.github.io/mkdocs-material/customization/
		* https://squidfunk.github.io/mkdocs-material/creating-your-site/#advanced-configuration 
	* Some themes and extensions listed here: https://hub.docker.com/r/minidocks/mkdocs