# Network IDs and Subnet Masks

## CIDR Notation

CIDR stands for Classes Inter Domain Routing. CIDR notation looks like an IP address but with a varying amount of un-set values and a slash appended to the end. After the slash is a value that represents how many binary digits are already spoken for in the subnet mask.

> In CIDR notation the network ID is the first part (192.168.1.0) and the number of bits in the subnet mask is the slash after the network ID (/24).

The subnet mask refers to the number of bits in the subnet mask and is a short representation of the entire  set of 4 [octets](Binary-Digits.md#^089948)

## Network IDs

Network IDs can be derived  by knowing an IP address a the subnet mask.

Starting with an example IP address of `192.168.40.55 `and a subnet mask of /21 (which translates to 255.255.248.0) we know that because the first two octets are 255, that in the network ID we should use the same numbers as in the IP address (192.168).

The third octet is more complicated. The [binary](/doc/binary-digits-O7iKdAOC0n) representation of the third octet is IP address is `00101000 `. The binary representation of third octet of the subnet mask is different at `11111000 `.

The third octet of the network can only be bits specified by the mask. So in this context,  the mask says the first five bits are spoken for so the decimal representation of the third octet of network ID must  40. The table below show the working of that:

|    | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|----|----|----|----|----|----|----|----|----|
| Mask | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 |
| IP Address | 0 | 0 | 1 | 0 | 1 | 1 | 0 | 1 |


## Examples 

| CIDR Subnet Mask | Binary | Decimal Subnet Mask |
|----|----|----|
| /24 | 1111111.11111111.11111111.00000000 | 255.255.255.0 |
| /16 | 11111111.11111111.00000000.00000000 | 255.255.0.0 |
| /21 | 11111111.11111111.11111000.00000000 | 255.255.248.0 |
| /26 | 11111111.11111111.11111111.11000000 | 255.255.255.192 |


## Process To Calculate Network ID

When required to work the CIDR network ID from a given **netmask** and **IP address, the process is as follows:**


1.  Identify in the network the Octets whose bits are all ones
2. Convert non-full octets to their [binary](/doc/binary-digits-O7iKdAOC0n) representations
3.  Convert the corresponding octet in the IP address to binary
4. Disregard any bits that fall after the full bits in the network mask
5. Calculate the decimal value of the remaining bits that fall before the full bits in the network mask.

## Calculating Broadcast Address

It is possible to calculate the Ipv4 Broadcast Address of a network  from it’s CIDR network ID and subnet mask.

For a network: 192.168.45.0/26 (255.255.255.192) we could work out the broadcast address from the binary representation of the fourth octet of the subnet mask (11000000). Here the last octet of the broadcast address  would be one less than the last used bit in that subnet mask fourth octet: 64-1 = 63

Broadcast Address = 192.168.45.63 

> The number of available addresses on a given subnet is 1 less than  last octet of the broadcast address  

For this network and broadcast address we would have 62 usable IP addresses.  