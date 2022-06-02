# Binary Digits

IP addresses are constructed in binary Octets. An Octet is a group of 8 binary digits. All IP addresses, subnet masks etc are made up of **4 Octets**. This totals to 32 binary digits.

### Binary Octets


Using the **binary doubling chart** you can work out the decimal value of an octet:

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|----|----|----|----|----|----|----|----|
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |

The above Octet would equal: **127**

This can be worked out in two ways for this specific octet:

```
1 + 2 + 4 + 8 + 16 + 32 + 64 = 127
```

In this specific Octet all numbers up until the last binary position are 1s, so the rule that **if all binary positions are filled on one side, the value is 1 less than first 0 valued binary position**. 

So in this example, 128 - 1 = 127


All ones in an Octet always equals  **255**. 


### IP Address In Binary   

When calculating the binary representation of an IP address always start from the highest number (128) in the table. It the number you are looking at is lower than the highest number move on until you have a number lower than that.

For the example IP Address, **192.168.1.5,**  we can split it into it’s constituent binary digits.

In this example:

* 192
  * 128 + 64 = 192
  * Therefore, 128 and 64 positions are on.
* 168
  * 128 + 64 != 168
  * 128 + 32 != 168
  * 128 + 32 + 16 != 168
  * 128 + 32 + 8 = 168
  * Therefore, 128, 32 and 8 positions are on.  
* 1
  * This simply means the 1 position is 1
* 5
  * 4 + 2 != 5
  * 4 + 1 = 5
  * Therefore, 4 and 1 positions are on.


**192.168.1.5 = 1100000.10101000.00000001.00000101**


This can be represented in the table below: 

| 192 | 168 | 1 | 5 |
|----|----|----|----|
|    |    |    |    |
| 11000000 | 10101000 | 00000001 | 00000101 |


\

## 