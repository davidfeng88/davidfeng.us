---
title: "Hugo"
date: 2026-07-10T21:56:30-04:00
tags: ["Hugo"]
images: []
---

- Quick Reference
	- Create a new single page
		- `hugo new posts/a/index.md`
		- `index.zh-cn.md` for Chinese version
	- Local preview at  `localhost: 1313`
		- `hugo server`  ( `-D`  to include drafts)
	- Update all submodules
		- `git submodule init`
		- `git pull --recurse-submodules` or `git submodule update --remote --merge`
	- version
		- `hugo version` show current version
		- `brew upgrade hugo` upgrade to latest version
    - If a page bundle is Chinese only
        - no need to have index.md placeholder
        - use `test.jpg` in index.zh-cn.md to refer to the `test.zh-cn.jpg` file
            - `![](test.jpg)` and `figure` shortcode both work
- doc style themes
	- Learn https://learn.netlify.app/en/
		- good for linear tutorial
	- Doks https://doks.netlify.app/
		- contains both docs and blog session and look good
		- search only shows page. no highlight within context.
		- Next blog theme?! Sell myself as a product?
	- Book https://hugo-book-demo.netlify.app/
		- used to use this one. does not look that good
	- Geekdocs https://geekdocs.de
		- similar to book but looks slightly nicer
	- Docsy https://example.docsy.dev/
		- comes from google. does not look that good.
	- other options
		- GitBook
			- limited theme (no dark mode)
			- folder is a mess
			- but it's simple to host
		- mkdoc-material https://github.com/squidfunk/mkdocs-material
			- uses python, so build time will be long.
			- config looks complicated.
