---
share: true

category: Linux
---
# Direnv

A tool to create directory specific .env files. Each will get loaded by the shell when entereing the directory.

## Snippets

### Shell Integration

```fish
direnv hook fish | source
```

### Add env variable

echo "export WHATEVER=variable" > .envrc
direnv allow

