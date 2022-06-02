---
share: true

category: Linux
---
- ### `du`

  This command is very useful as it will return disk usage for a specific file path and to a specific directory depth.

  Examples:

  - `du path/to/file` Recursively returns disk usage for all files from the specified path
  - `du -h --max-depth=2 path/to/file` Will output disk usage recursively a maximum of two levels down from the specified path and print the file sizes in human readable form
  - `du -sh path/to/file` Does the same as above except will only print the size of file/directories in the current directory