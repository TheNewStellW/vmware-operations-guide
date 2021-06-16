# VMware Operations Guide

This repo contains the contents of Iwan Rahabok's VMware Operations Guide (https://via.vmw.com/OpsMgmt), ported to Markdown and built into a static site using Hugo.

![](readme/screenshot.png)

# Build the site

1. Install Hugo (https://gohugo.io/)

```bash
brew install hugo
```

1. Clone this repo to your machine
`git clone https://gitlab.eng.vmware.com/wstellios/vmware-operations-guide.git && cd vmware-operations-guide`

1. Run a local Hugo server
`hugo server -D`

1. Go to http://localhost:1313 and see the live build of the static site

# Why Markdown?

Have a read here: https://learn.netlify.app/en/cont/markdown/.

The short version:

Let’s face it: Writing content for the Web is tiresome. WYSIWYG editors help alleviate this task, but they generally result in horrible code, or worse yet, ugly web pages.

Markdown is a better way to write HTML, without all the complexities and ugliness that usually accompanies it.

Some of the key benefits are:

- Markdown is simple to learn, with minimal extra characters so it’s also quicker to write content.
- Less chance of errors when writing in markdown.
- Produces valid XHTML output.
- Keeps the content and the visual display separate, so you cannot mess up the look of your site.
- Write in any text editor or Markdown application you like.
- Markdown is a joy to use!

# Managing content

Each HTML page on the website is defined by two things: 1) A folder path and 2) a `_index.md` file. This folder path/file combo is all stored under `/content`. For example, the `Acknowledgement` page is defined under `/content/Acknowledgement/_index.md`. Acknowledgement is the "Page", and the `_index.md` file is the page content. Pages can have sub-pages, turning them more into "Sections" and "Sub-sections". Take a look at `/content/Operations Management`, it has a `_index.md` file along with sub-folders. Each sub-folder has another `_index.md` file and even more sub-folders. This layout provides maximum flexibility in organising the content as well as prefacing all sections and chapters for this book.

## Creating a new page

First, find out ahead of time where your new page will exist in the document tree. Let's use an example. I want to create a new page under `Operations Management > Chapter 2 - Performance Management` called `Plan | Monitor | Troubleshoot | Optimize`. However, we want to maintain a consistent page numbering underneath "Chapter 2 - Performance Management". You'll notice that Chapter 2 - Performance Managment has 2 other sub-sections (1.2.1 and 1.2.2) so this new page will be prefixed with `1.2.3` leaving us with `1.2.3-plan-monitor-troubleshoot-optimize`. But, that only names the folder. And if we want a page to display for this folder we must include a `_index.md` file. In the root directory of the repo, you can run this command to create the new page: `hugo new "Operations Management/Chapter 2 - Performance Management/1.2.3-plan-monitor-troubleshoot-optimize/_index.md"`

## Front matter

Every page has **front matter** which is basically metadata about the page. If you used the page creation method above, you'll get the basic front matter included, with the date automatically populated:

```markdown
---
title: "VMware vRealize Operations Management"
date: 2021-06-11T11:31:22+10:00
draft: true
---
```

This front matter can be used to control a page's visibilty during publishing by using the `draft: true` flag, or control the published date with the `date: yyyy-mm-dd` flag. Front matter will always need a `title: ""` value.

## Page Content

All content is written in Markdown. 

### Images and Attachments

If you wish to include images or attachments, simply include the file in the same directory as your page's `_index.md`. This keeps all the material together for the page. 
