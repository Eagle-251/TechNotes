---
dg-publish: 

category: SysAdmin
---



For remote ssh I use my an [authentication subkey](https://www.linode.com/docs/guides/gpg-key-for-ssh-authentication/) of my [pgp key](https://gilchrist.scot/.well-known/openpgpkey/hu/esfzao74zw7on5f8ickbk4htbj1js7nb) in place of a regular ssh key.

As I use [fish](fishshell.com/), I load the `gpg-agent` in place of `ssh-agent`, set the correct `tty` and launch `gpg-agent`

```fish
set -e SSH_AUTH_SOCK
set -U -x SSH_AUTH_SOCK (gpgconf --list-dirs agent-ssh-socket)

set -x GPG_TTY (tty)

gpgconf --launch gpg-agent
```

On the server, I put the output of `gpg --export-ssh-key ewan@gilchrist.scot` into `~/.ssh/authorized_keys`. This will me to login to the server using my gpg key.

I also have an entry in `.ssh/config` for this server:

```
Host gilchrist.scot
	Hostname <vpn-ip>
	User ewan
	Port <non-standard-port>

```