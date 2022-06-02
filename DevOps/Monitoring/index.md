---
share: true

category: Monitoring
---
# Monitoring

This is a collection of tools and snippets in relation to monitoring a running linux system. This is mainly focused on monitoring headless systems, but could still apply to systems running a desktop environment.

Areas of concern for monitoring a linux systems could be:

- [System Stats](#system-stats)
- [Process Monitoring](#process-monitoring)
- [Network](#network)
- [Logs](#logs)
- [User Management](#user-management)

[Example Monitoring Report on a VPS](report.md)

## System stats

System statistics on a Linux system could refer to a number of things. It could be hardware statistics, processing resource use, energy use etc. There is a lot of overlap with [Process Monitoring](#process-monitoring) so in order to satisfy [DRY](https://wikiless.org/wiki/Don%27t_repeat_yourself?lang=en) I will focus on tools and methods to query static information about the Linux systems state.
### Tools
- [uname](../../Linux/CLI-Tools/uname.md)
- [lshw](../../Linux/CLI-Tools/lshw.md) 
- [lsusb](../../Linux/CLI-Tools/lsusb.md)
- [lspci](../../Linux/CLI-Tools/lspci.md)
- [lsblk](../../Linux/CLI-Tools/lsblk.md)
- [df](../../Linux/CLI-Tools/df.md)
- [du](../../Linux/CLI-Tools/du.md)

## Process Monitoring
### Tools

- [ps](../../Linux/CLI-Tools/ps.md)

- [top](../../Linux/CLI-Tools/top.md)

- [htop](../../Linux/CLI-Tools/htop.md)

## Network

There are many linux utilities to monitor networks and network traffic.
They range from simple utilities that return the static state and/or configuration
of network interfaces to complex network monitoring tools.

- ### `ping`

  Ping is a simple but extremely useful tool for monitoring the network connectivity and latency of network of a linux system. It send `ICMP ECHO_REQUEST` packets to a specific host and waits for the reply. The time between the sending and receiving of the packet is returned to the user in ms. This value can be a useful proxy for the latency of a network.

  Examples:

  - Send pings to google.com every second until the user exits the program:<br>`ping google.com`

  - Send 4 pings to google.com then exit: <br> `ping -c 4 google.com`

  - Send 4 pings with an interval of 3 seconds between pings:<br> `ping -i 3 -c 4 google.com`

  - Ping google.com using a specific interface (useful to diagnosing the latency of vpn): <br> `ping -I <interface_name> google.com`

- ### `ip`

  `ip` is a utility to show and set routes, create and bring up/down network interfaces, devices and tunnels.
  The command has many "objects" that fulfill different functions:

  | Object                   | Use                                                 |
  | ------------------------ | --------------------------------------------------- |
  | `address`                | protocol (IP or IPv6) address on a device.          |
  | `addrlabel`              | label configuration for protocol address selection. |
  | `l2tp`                   | tunnel ethernet over IP (L2TPv3).                   |
  | `link`                   | network device.                                     |
  | `maddress`               | multicast address.                                  |
  | `monitor`                | watch for netlink messages.                         |
  | `mptcp`                  | manage MPTCP path manager.                          |
  | `mroute`                 | multicast routing cache entry.                      |
  | `mrule`                  | rule in multicast routing policy database.          |
  | `neighbour`              | manage ARP or NDISC cache entries.                  |
  | `netns`                  | manage network namespaces.                          |
  | `ntable`                 | manage the neighbor cache's operation.              |
  | `route`                  | routing table entry.                                |
  | `rule`                   | rule in routing policy database.                    |
  | `tcp_metrics/tcpmetrics` | manage TCP Metrics                                  |
  | `token`                  | manage tokenized interface identifiers.             |

  The most common of these however are address, route and link object. Most of the objects will return their configuration with no arguments and will allow you to `set` a config depending on the object called.

  Examples:

  - Return address information if all network interfaces on the system: <br> `ip address`

  - Show link layer information for all network interfaces: <br> `ip link`

  - Output the routing table for the system: <br> `ip route`

  - Add a new network interface: <br> `ip addr add ip/ dev <interface_name>`

- ### `netstat`

  Netstat could be seen as the monitoring equivalent to `ip`. It has mostly been succeeded by `ss` and `ip`. It can be very useful when deploying applications as it allows you to check if a port has already been bound by another application.

  Examples:

  - List all ports being used, open or not: <br> `netstat --all`

  - List all open ports: <br> `netstat -l`

  - List all ports being used to transfer TCP Segments: <br> `netstat -t`

  - The same as above but show UDP datagrams: <br> `netstat -u`

  - Use a combination of the above with `grep` to check a specific port (including privileged ports): <br> `sudo netstat -tunlp | grep <port-number>`

- ### `ss`

  todo

- ### `nslookup`

  Query the configured DNS nameserver for a particular record. This command defaults to A records unless specified.

  Examples:

  - Look up the A records of google.com: <br> `nslookup google.com`

  - Specify a DNS server different from the system configured nameserver: <br> `nslookup google.com 1.1.1.1`

  - Lookup the MX (mail exchange) records of google.com: <br> `nslookup -type=MX google.com`

  - Return a reverse DNS lookup (PTR record) for Cloudflare DNS: <br> `nslookup -type=PTR 1.1.1.1`

- ### `dig`

  Dig is very similar to nslookup but is more flexible and can be more useful for troubleshooting DNS record issues.

- ### `whois`

- ### `nmap`

- ### `nc`

- ###

## Logs

Logging in most major Linux distributions is usually handled by journald, with some important exceptions for example apt/apt-get on Debian/Ubuntu does not log to systemd but it uses syslog.

The main difference being that journald logs to binary files that can be only read with the utility `journalctl` whereas syslog logs to [RFC5424](https://tools.ietf.org/html/rfc5424) compliant log files.

### Syslog

Syslog is both a logging daemon and logging messages format. Rsyslog is the daemon that handles log messages and is configured in `/etc/rsyslog.conf` and in drop-in configuration files in the `/etc/rsyslog.d` directory which are added via an "include" in the main conf file.
Here specific locations for logs from specific daemons or applications are set.

For example:

`auth,authpriv.* /var/log/auth.log`

This line in `/etc/rsyslog.conf` tell syslog to store logs from authentication utilities (eg pam, sudo) to the `auth.log`.

### Journald

Journald is logging component of the [systemd](https://wikiless.org/wiki/Systemd?lang=en) init system. Systemd is utilises plain text `unit` files of various types to manage the state of the system at various stages of the boot process. These stages are known as `targets`. The system moves progressively through each of these targets until it reaches the last target, usually the `user-session` target.

Each systemd unit has it's own log which can be accessed through the `journalctl` binary.
Unlike syslog, journalctl (when executed with no arguments) can return logs of all the systemd units in one stream. <br>
You can specify a particular unit file however by using the `-u` flag:

- `journalctl -u avahi-daemon.service`

Including the `-f` will follow log output in real time:

- `journalctl -fu avahi-daemon.service`

Journald also splits up logs by boots. This will show all logs from the current boot:

- `journalctl -b`

## User Management