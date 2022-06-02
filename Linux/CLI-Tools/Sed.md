---
share: true

category: Linux
---

# Sed

## Snippets

Replace the same in line in multiple markdown files in one folder:
```shell
find $PWD -type f -name "*.md" -exec sed -i "s/dg-publish: true/share: true/g" {} \;
```

Multi-line version:
```shell
find $PWD -type f -name "*.md" -exec sed -zi "s/eleventyNavigation:\n  key: .*\n  parent:/category:/g" {} \;
```
