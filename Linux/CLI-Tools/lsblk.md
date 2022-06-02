---
share: true
category: Linux
---
- ### `lsblk`

  This will print all block devices in a tree like format.

  Examples:

  - `lsblk -f` Print block filesystem information alongside block info
  - `lsblk --exclude 7` Exclude a specific device type, one integer defaults to the `MAJ` number aka device type
    This specific command will exclude snap loop devices from the command output.
