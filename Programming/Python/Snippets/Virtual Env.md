---
dg-publish: 

category: Snippets
---

# Python Virtual Environments
When running python projects, it is important not to influence the existing modules of the system Python.
Virtual Environments utilise a local python workspace, where modules will be installed. This is useful when running someone elses project or when developing.

## Installation
### Fedora 
```shell
sudo dnf install python3-virtualenv
```


## Usage
In python 3 it is sufficient to run:

```shell
virtualenv <projectname>
```

To activate:

```shell
source <projectname>/bin/activate
```

To deactivate:

```shell
deactivate
```
