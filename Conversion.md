# Commands used to clean text from Word

Recursively searches through MD files and removes UTF-8 right-side curled apostrophes, also known as `xe2 x80 x99`

```bash
find . -type f -name "*.md" -print0 | xargs -0 sed -i '' "s/`printf "\xe2\x80\x99"`/'/g"
```

