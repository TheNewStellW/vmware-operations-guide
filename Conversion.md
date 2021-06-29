# Commands used to clean text from Word

Use this to search and replace characters in content directory:

```bash
find . -type f -name "*.md" -print0 | xargs -0 sed -i '' "s/<characters to remove>/<characters to insert>/g"
```

Use this to identify all non-ascii characters

```bash
pcregrep -r --color='auto' -n '[^[:ascii:]]' .
```