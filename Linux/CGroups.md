---
share: true

category: Linux
---

# CGroups

CGroups (Control Croups) are a way to limit the resources allocated to, and accessible by, a given program or process. CGroups can cover usage of CPU, Memory, disk I/O, network and more.
The use of CGroups is particularly when seeking containerise a program, as it gives the admin/system a way to make sure resources are distributed evenly and not allow any one resource hungry application disrupt others.
Most container systems rely heavily on CGroups for their basic function.

The CGroups functionality has been part of the Linux MainlineKernel since 2007 in version 2.6.24.