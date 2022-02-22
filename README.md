# Net_Practice
[My solution](https://github.com/tblaase/Net_Practice/my_solutions) and basic explanantion on Net_Practice and networking basics.<br>

First of all, thanks to [Robin | radelwar](https://github.com/Radel-24) for explaining the more in depth stuff to me.<br>
This may not be perfect since i just learned about all of the following myself.<br>
So please, if there is anything wrong or missing, please notify me by reaching out to me ([my profile](https://github.com/tblaase)) or create an [issue](https://github.com/tblaase/Net_Practice/issues/new), thanks.<br>


I only created this tutorial, since the project has a few flaws and you have the ability to solve it in a way thats wrong, but the project is still telling you that everything is correct.<br>
And all other tutorials i found used these flaws to simplify the solution.<br>

## Contents
- [Basics](https://github.com/tblaase/Net_Practice#basics)
  - [special IP-ranges](https://github.com/tblaase/Net_Practice#special-ip-ranges)
  - [Masks](https://github.com/tblaase/Net_Practice#masks)
  - [Switches](https://github.com/tblaase/Net_Practice#switches)
  - [Routers](https://github.com/tblaase/Net_Practice#routers)
  - [Routing Tables](https://github.com/tblaase/Net_Practice#routing-tables)
- [Levels](https://github.com/tblaase/Net_Practice#levels)


## Basics
For this project we only use IPv4, so i won't talk about IPv6.<br>
An IPv4-adress is a 32-bit number divided into 4 "blocks", each 8 bits.<br>
i.e.:<br>
`192.168.100.1` turns into `11000000.10101000.01100100.00000001`<br>
So the min. value of one "block" is `0` and the max. value is `255`.<br>
The same logic applies to the network-mask:<br>
`255.255.255.0` turns into `11111111.11111111.11111111.00000000`<br>
Special to the mask is, after one bit was `0` there can't be any `1` bit's anymore.<br>
so the only available numbers are:


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
and `255.255.128.128` would **not** be a valid mask.<br>
<br>
In order to have the ability to send packages between two IP-addresses they either need to be part of the same network or they need to be connected by a router which is part of both subnets.


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


The number of usable IP-addresses per subnet is lower than the total number of IP's because the first address is reserved as the network-address of the subnet and the last address is reserved as a broadcast-adress.<br>
i.e. for mask `255.255.255.252`:<br>
broadcast: `190.3.2.255`<br>
network: `190.3.2.252`<br>
usable IP's: `190.3.2.253`, `190.3.2.254`


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Switches

A switch will enable you to connect more than two devices to the same network.<br>
It's only purpose is to distribute packages to its network.<br>

## Routers

As previously mentioned a router is a interface which enables communication between different networks.<br>
A router has the ability to be part of multiple networks, in Netpractice this is visualized by the so called `Interface`.<br>
If routers and switches are still magic to you, i suggest looking deeper [into it](https://www.youtube.com/watch?v=Vc16CCAAz7Q) yourself, as their basic understanding is crucial to succeed in this project.


[back to contents](https://github.com/tblaase/Net_Practice#contents)

![example_router](https://github.com/tblaase/readme_additions/router_example.png)

## Routing Table
The routing table is there to store all the different paths to all the networks, the device is part of.<br>
In Net_Practice the routing table consists of two elements, the **destination** and the **next hop**<br>
The **destination** consists of the network-address that you want to send a package to, combined with the CIDR of that network: `190.3.2.252/30`. If you don't want to specify a destination, you can just set it to `default` or `0.0.0.0/0`.<br>
The **next hop** is the address of the next router that you need to send the packages to in order to reach the destination-network.<br>


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Levels

Here are all the solutions to all 10 Levels, with short explanations.<br>
<details>
  <summary>Level 1</summary>
  ![Level 1](https://github.com/tblaase/my_solutions/Level_1.png)<br>
</details>
<details>
  <summary>Level 2</summary>
  ![Level 2](https://github.com/tblaase/my_solutions/Level_2.png)<br>
</details>
<details>
  <summary>Level 3</summary>
  ![Level 3](https://github.com/tblaase/my_solutions/Level_3.png)<br>
</details>
<details>
  <summary>Level 4</summary>
  ![Level 4](https://github.com/tblaase/my_solutions/Level_4.png)<br>
</details>
<details>
  <summary>Level 5</summary>
  ![Level 5](https://github.com/tblaase/my_solutions/Level_5.png)<br>
</details>
<details>
  <summary>Level 6</summary>
  ![Level 6](https://github.com/tblaase/my_solutions/Level_6.png)<br>
</details>
<details>
  <summary>Level 7</summary>
  ![Level 7](https://github.com/tblaase/my_solutions/Level_7.png)<br>
</details>
<details>
  <summary>Level 8</summary>
  ![Level 8](https://github.com/tblaase/my_solutions/Level_8.png)<br>
</details>
<details>
  <summary>Level 9</summary>
  ![Level 9](https://github.com/tblaase/my_solutions/Level_9.png)<br>
</details>
<details>
  <summary>Level 10</summary>
  ![Level 10](https://github.com/tblaase/my_solutions/Level_10.png)<br>
</details>


[back to contents](https://github.com/tblaase/Net_Practice#contents)
