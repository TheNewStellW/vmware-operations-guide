# VMware Operations Guide

This repo contains the contents of Iwan Rahabok's [VMware Operations Guide](https://via.vmw.com/OpsMgmt), ported to Markdown and built into a static site using Hugo.

![](readme/screenshot.png)

The entire site is static and built using the static site generator [Hugo](https://gohugo.io/). Hugo uses HTML/CSS, Markdown files, and a templating engine to generate a static site that can be hosted almost anywhere. This is a great model for an online book, as the Markdown files can be parsed by Pandoc and made into EPUB, MOBI and PDF files quite easily.

# License

Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

# Table of Contents

1. [Why Markdown?](#why-markdown)
2. [Content Organisation](#content-organisation)
3. [Contributing](#contributing)

# Why Markdown?

There's no point trying to improve on a great write up. Read this [Why Markdown?](https://learn.netlify.app/en/cont/markdown/) post to see why I selected this format.

For your convenience, here's an excerpt:

>Let’s face it: Writing content for the Web is tiresome. WYSIWYG editors help alleviate this task, but they generally result in horrible code, or worse yet, ugly web pages.
>
>Markdown is a better way to write HTML, without all the complexities and ugliness that usually accompanies it.
>
>Some of the key benefits are:
>
> - Markdown is simple to learn, with minimal extra characters so it’s also quicker to write content.
> - Less chance of errors when writing in markdown.
> - Produces valid XHTML output.
>- Keeps the content and the visual display separate, so you cannot mess up the look of your site.
> - Write in any text editor or Markdown application you like.
> - Markdown is a joy to use!

# Content Organisation

In Hugo, "pages" are the core of your site. This book uses Hugo [Page Bundles](https://gohugo.io/content-management/organization/#page-bundles) to represent each page that is generated.

The structure on disk ends up looking like this:

```
.
└── content
    ├── Acknowledgements
    |   └── _index.md  // <- https://example.com/content/acknowledgements/
    ├── Dashboards
    |   ├── _index_.md   // <- https://example.com/content/dashboards/
    |   └── Chapter 1 - Design Considerations
    |       ├── _index.md  // <- https://example.com/dashboards/chapter-1-design-considerations/
    |       └── 3.1.1-dashboard-alert-report
    |           └── _index.md // <- https://example.com/dashboards/chapter-1-design-considerations/3.1.1-dashboard-alert-report/
    └── Metrics
        ├── _index_.md   // <- https://example.com/content/metrics/
        └── Chapter 1 - Overview
            ├── _index.md  // <- https://example.com/metrics/chapter-1-overview/
            └── 2.1.1-nuances-in-metrics
                └── _index.md // <- https://example.com/metrics/chapter-1-overview/2.1.1-nuances-in-metrics/
```

The result leaves us with appropriate folders for each and every page to contain not only the `_index.md` file but any supporting materials (documents, images, attachments, etc). 

## Page Bundles

Every page underneath a chapter is represented by a folder with an `_index.md`. This folder/_index.md combination is called a [Page Bundles](https://gohugo.io/content-management/organization/#page-bundles). The Page Bundle naming convention follows the same section, chapter and heading values in use in the source material (Iwan's book). Every leaf Page Bundle is prefixed with the **Part#**-**Chapter#**-**Heading#** followed by the title of the page. Look at the directory structure above. Dashboards is Part **3** in Iwan's book, and underneath it is Chapter **1**, with a page titled "**Dashboard, Alert, Report**". The resulting page bundle name is **3.1.1-dashboard-alert-report** (replacing breaks between words with hyphens).

In many Page Bundles, images exist to support the page. These follow the same naming convention as the page bundles, but instead of the title, I append **fig-X** to the file instead. To continue the example above, that leaves me with **3.1.1-fig-1.png**, **3.1.1-fig-2.png** and so on.

# To do 

- [ ] Readme: Write style guide
- [ ] Readme: Write writing guide
- [ ] Book: Review all pages and return missing intra-document links
- [ ] Book: Refactor Page Bundles that rely heavily on HTML to Markdown