---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }} ## This is the first published date
draft: true # When true, the page will not be processed and displayed on the website. Set to false for the page to be generated and published.
weight:  # Integer - Used to influence the order that pages are displayed to readers, in the sidebar as well as using the nav arrows.
chapter: false # If true, centers all text and removes built in table of contents to represent a chapter page.
disableToc: false # Disables on-page table of contents that displays all headers of the page.
disableReadingTime: false # Disables reading time on the page
---