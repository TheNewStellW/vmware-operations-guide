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