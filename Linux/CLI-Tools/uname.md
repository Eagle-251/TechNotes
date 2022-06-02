---
share: true
category: Linux
---
- ### `uname`

  This command will _"Print certain system information"_ about the system.
  This command will provide generic static information about your system. FOr example the kernel version, the hostname, the instruction set architecture, processor type and the operating system type.
  This command can be very useful in scripts intended to be run on systems with differing architectures. For example, it could be used in a script to download the correct Goland binary for your system:

  - `https://go.dev/dl/go1.17.7.linux-$(uname -i).tar.gz"`