---
share: true
category: Shells
---
# Fish
### Common Tasks

**Add To Path**

Call the inbuilt function `fish_add_path`, use `-a` to append to the existing path:
- `fish_add_path -a $HOME/.local/bin`

**Create an Alias**
Similar syntax to [[Tech_Notes/Shells/Bash]]:
- `alias ls "ls -al"`
Unlike [[Tech_Notes/Shells/Bash]], fish takes care of persistence of the alias through the `funcsave` function:
- `funcsave ls`

