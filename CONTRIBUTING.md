# Contributing

You can contribute to this book by submitting a pull request with your changes. Any changes will be reviewed for accuracy and document structure before being accepted.

If you do not want to submit a PR, you can always file an Issue for it to be addressed by a repo maintainer.

## Getting Started

If you'd like to work on this book on your local machine, you'll need [Hugo](https://gohugo.io/) and a text editor. That's pretty much it! I use VS Code but you could use whatever you want.

1. Install Hugo for [macOS](https://gohugo.io/getting-started/quick-start/#step-1-install-hugo) or [Windows](https://gohugo.io/getting-started/installing)
1. Clone this repo: `git clone <to be included>`
1. Change to the repo directory `cd vmware-operations-guide`
1. Start a Hugo server with live render: `hugo server`
1. Open your browser and go to `http://localhost:1313`

With Hugo running in the background, you can see your changes live in the browser as you make them.

## Creating a new page

Identify where your new page will exist in the folder structure (check the `content` folder). Is it a new page for Dashboards Chapter 1 `content/Dashboards/Chapter 1 - Design Considerations/`? Maybe it's a new page for Metrics Chapter 6 `content/Metrics/Chapter 6 - Other Metrics/`?

In either case, you'll need to know the path. You'll also need to know the page title and the numerical identifier. You'll need these values to run `hugo new` to create the page bundle.

### Example Page

For now, I'll provide an example. Let's say you want to create a new page titled "Super Metrics - Friend or Foe" in **Chapter 4 - Super Metrics** under **Miscellaneous**. You can see that 4 Page Bundles already exist, which would make yours number **5**. The new name for your Page Bundle would be "4.4.**5**-super-metrics-friend-or-foe". You could go ahead and make the folder and _index.md file yourself, or, you can use Hugo to create the entire Page Bundle for you using the `hugo new` command like this: `hugo new "Miscellaneous/Chapter 4 - Super Metrics/4.4.5-super-metrics-friend-or-foe/_index.md`

## Front Matter

Every page has **front matter**. Front matter is metadata about the page that exists at the beginning of the Markdown file. If you used the page creation method above, your new page will have the default front matter included, with the date automatically populated. It will look like this:

```markdown
---
title: "x.x.x-my-page-title"
date: 2021-06-11T11:31:22+10:00
draft: true
---
```

This front matter specifies many attributes, but for this book, only the basics are used: 

- Title: The title of the page. Display on sidebars and menu's and the top of the rendered page.
- Date: Refers to the date the file was created. Is typically auto-populated by the `hugo new` command but can be updated by the author.
- Draft: true/false. If set to true, the page will not be rendered when you run `hugo`. If set to false, it will render. You can live render any drafts you're working on using `hugo server -D`
- Chapter: true/false. Used only on Chapter pages.
- Weight: integer. Used to dictate relative weight when ordering pages in the sidebar. The lower the number, the higher priority it will have in the list.

## Page Content

All content is written in Markdown. See the [Why Markdown?](readme.md#why-markdown) section above.

However, there are a lot of things that Markdown doesn’t support well. You could use pure HTML to expand possibilities. But this happens to be a bad idea. Everyone uses Markdown because it’s pure and simple to read even non-rendered. You should avoid HTML to keep it as simple as possible.

To avoid this limitations, Hugo created shortcodes. A shortcode is a simple snippet inside a page. Some small details throughout the online book are achieved through shortcodes.

### Images and Attachments

If you wish to include images or attachments, include the file in the Page Bundle you want to use it in (same directory as your page's `_index.md`) with a name that matches [the naming convention](#page-bundles). This will keep related content together. 

#### Images

To reference an image in a page using Markdown: `![](filename.ext)`.

#### Attachments

Attachments should exist in a **page.files** folder within a Page Bundle like so:

> - content
>   - _index.md
>   - page
>      - _index.md
>      - **page.files**
>        - attachment.pdf

To list the page bundle attachments on the page, use the Attachments shortcode:

```
{{% attachments title="Related files" pattern=".*(pdf|mp4)" /%}}
```

Which renders to something like this:

![](readme/attachments.png)

For more information on attachments, read the theme's [documentation on shortcodes](https://learn.netlify.app/en/shortcodes/attachments/). 

## Style Guide

> Placeholder

## Writing Guide

> Placeholder