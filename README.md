# Net_Practice
[My solution](https://github.com/tblaase/Net_Practice/my_solutions) and basic explanantion on Net_Practice and networking basics.<br>

This may not be perfect since i just learned about all of the following myself.<br>
So please, if there is anything wrong or missing, please notify me by reaching out to me ([my profile](https://github.com/tblaase)) or create an [issue](https://github.com/tblaase/Net_Practice/issues/new), thanks.<br>

## Contents
- [Basics](https://github.com/tblaase/Net_Practice#basics)
  - [special IP-ranges](https://github.com/tblaase/Net_Practice#special_ip-ranges)
  - [Masks](https://github.com/tblaase/Net_Practice#masks)
  - [Routers](https://github.com/tblaase/Net_Practice#routers)
- [Levels](https://github.com/tblaase/Net_Practice#levels)


## Basics
For this project we only use IPv4, so i won't talk about IPv6.<br>
Here is the basics of how ip-routing and network-masks work:<br>
An IPv4-adress is a 32-bit number divided into 4 "blocks", each 8 bits.<br>
i.e.:<br>
`192.168.100.1` turns into `11000000.10101000.01100100.00000001`<br>
So the min. value of one "block" is `0` and the max. value is `255`.<br>
The same logic applies to the network-mask:<br>
`255.255.255.0` turns into `11111111.11111111.11111111.00000000`<br>
Special to the mask is, after one bit was `0` there can't be any `1` bit's anymore.<br>
so the only available numbers are:<br>
- `255`
- `254`
- `252`
- `248`
- `240`
- `224`
- `192`
- `128`
- `0`



Through which `255.255.255.0` would be a valid mask<br>
and `255.255.128.128` would *not* be a valid mask.<br>
<br>
In order to have the ability to send packages between two IP-addresses they either need to be part of the same subnet or they need to be connected by a router which is part of both subnets.


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Special IP-ranges

The following special address-ranges are reserved for Private Networks:<br>
`10.0.0.0 – 10.255.255.255`<br>
`172.16.0.0 – 172.31.255.255`<br>
`192.168.0.0 – 192.168.255.255`<br>

The following address-range is reserved for so called loopback addresses:<br>
`127.0.0.0 – 127.255.255.255`


There is some more special ip-ranges, but for this project, you only need to remember those above.


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Masks

The network-mask, subnet-mask or in our project only called mask is there to decide which range of ip-adresses are part of the same subnet.<br>
There is 2 different ways of writing the mask:

- "Dot-decimal notation": `255.255.255.0`
- "Class Inter-Domain Routing" or "CIDR": `/24`


The more usable ip-addresses you need in one subnet, the less subnets you will be able to create.<br>
To help you understanding it, i found this table very helpfull:


| CIDR | Dot-decimal | Number of IP-addresses<br /> per subnet | Usable IP-addresses <br /> per subnet | Number of subnets |
| :---: | :-----------: | :---: | :---: | :---: |
| /32 | 255.255.255.255 | 1 | 0 | 256 |
| /31 | 255.255.255.254 | 2 | 1 | 128 |
| /30 | 255.255.255.252 | 4 | 2 | 64 |
| /29 | 255.255.255.248 | 8 | 6 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 32 | 30 | 8 |
| /26 | 255.255.255.192 | 64 | 62 | 4 |
| /25 | 255.255.255.128 | 128 | 126 | 2 |
| /24 | 255.255.255.0 | 256 | 254 | 1 |


The number of usable IP-addresses per subnet is lower than the total number of IP's because the first address is reserved as the network-address of the subnet and the last address is reserved as a broadcast-adress.


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Routers
As previously mentioned a router is a interface which enables communication between different subnets.<br>
To simplify things a little, for this project we think of the internet as just a router.<br>
A router has the ability to be part of multiple networks, this is done by the router having multiple IP-addresses:
![example_router](https://github.com/tblaase/readme_additions/example_router.png)
## Levels
<details>
  <summary>
  ### Level 1
  </summary>
  here should be the screenshot and explanation of Level 1.<br>
</details>
<details>
  <summary>### Level 2</summary>
  here should be the screenshot and explanation of Level 2.<br>
</details>


[back to contents](https://github.com/tblaase/Net_Practice#contents)
