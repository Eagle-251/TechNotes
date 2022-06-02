# The Class System

## IPV4 Classes

IP Classes are designed to provide a default mask based on the first octet. They precede the development of [Network-IDs-and-Subnet-Masks](Network-IDs-and-Subnet-Masks.md). Classes however did not provide enough IP addresses by only splitting up the first [octets](Binary-Digits.md#^089948).

There are three bits of information associated IPv4 classes, this is the **Class,** the **First Octet Range** and the **Default Mask.**

### Examples

| Class | 1st Octet Range | Default Mask |
|----|----|----|
| Class A | 1 - 126 | 255.0.0.0 |
| Class B | 128 - 191 | 255.255.0.0 |
| Class C | 192 - 223 | 255.255.255.0 |
| Class D | 224 - 239 | Multicasting |
| Class E | 240- 255.255.255.254 | Experimental |
| Loopback | 127 |    |

 


