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
  - [Level 1](https://github.com/tblaase/Net_Practice#level-1)
  - [Level 2](https://github.com/tblaase/Net_Practice#level-2)
  - [Level 3](https://github.com/tblaase/Net_Practice#level-3)
  - [Level 4](https://github.com/tblaase/Net_Practice#level-4)
  - [Level 5](https://github.com/tblaase/Net_Practice#level-5)
  - [Level 6](https://github.com/tblaase/Net_Practice#level-6)
  - [Level 7](https://github.com/tblaase/Net_Practice#level-7)
  - [Level 8](https://github.com/tblaase/Net_Practice#level-8)
  - [Level 9](https://github.com/tblaase/Net_Practice#level-9)
  - [Level 10](https://github.com/tblaase/Net_Practice#level-10)


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
| /31 | 255.255.255.254 | 2 | 0 | 128 |
| /30 | 255.255.255.252 | 4 | 2 | 64 |
| /29 | 255.255.255.248 | 8 | 6 | 32 |
| /28 | 255.255.255.240 | 16 | 14 | 16 |
| /27 | 255.255.255.224 | 32 | 30 | 8 |
| /26 | 255.255.255.192 | 64 | 62 | 4 |
| /25 | 255.255.255.128 | 128 | 126 | 2 |
| /24 | 255.255.255.0 | 256 | 254 | 1 |


The number of usable IP-addresses per subnet is lower than the total number of IP's because the first address is reserved as the network-address of the subnet and the last address is reserved as a broadcast-adress.<br>
i.e. for mask `255.255.255.252`:<br>
network: `190.3.2.252`<br>
broadcast: `190.3.2.255`<br>
usable IP's: `190.3.2.253`, `190.3.2.254`


[back to contents](https://github.com/tblaase/Net_Practice#contents)

## Switches

A switch will enable you to connect more than two devices to the same network.<br>
It's only purpose is to distribute packages to its network.<br>
To see a working example, you can take a look at [Level 3](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_3.png).<br>

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

Here are all the solutions and explanations to all 10 Levels.<br>

### Level 1

<details>
  <summary>show</summary>

  ![Level 1](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_1.png)<br>
  Here we have two separate networks, each consisting of two computers.<br>
  In order to make it work, the two computers need to be part of the same network.<br>
  Because the mask of A and B is `255.255.255.0` the possible IP-adresses of A1 are <br>`104.99.23.1 - 104.99.23.254`.<br>
  For C and D the mask is `255.255.0.0`, so the usable IP's are `211.191.0.1 - 211.191.255.254`


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 2

<details>
  <summary>show</summary>

  ![Level 2](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_2.png)<br>
  Here we have two separate networks again, but this time we need to set the mask and IP correctly.<br>
  For the network of A and B, they need the same mask, `255.255.255.224`.<br>
  The available IP-addresses for A1 are `192.168.57.193 - 192.168.57.221`.<br>


  Network C and D already has the same mask. so they just need addresses that are part of the same subnet.<br>
  In the case of the mask beeing `/30` the subnet only consists of 2 available addresses per subnet. So be carefull, to choose the correct ones. to make things easier, i suggest you either start with the lowest or highest subnet.<br>
  I choose the highest, so my available IP-range is `192.168.57.253 - 192.168.57.254`


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 3

<details>
  <summary>show</summary>

  ![Level 3](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_3.png)<br>
  In this level we have our first encounter with a [Switch](https://github.com/tblaase/Net_Practice#switches).<br>
  Since we can't manipulate the mask of C, `255.255.255.128` will be the mask of the whole network.<br>
  A has a fix IP, so the whole networks range will be `104.198.187.1 - 104.198.187.126`.


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 4

<details>
  <summary>show</summary>

  ![Level 4](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_4.png)<br>
  This is our first time running into a router, since the router does not connect to anything else, there is no routing table, that needs to be worked with.<br>
  A has a fixed IP, so this will define the IP of our network.<br>
  You can freely choose a fitting mask for the network, but the subnet has to have at least 3 usable IP-addresses, <br> so choosing `255.255.255.240`/`/28` will create a subnet of 14 usable addresses.<br>
  The fixed IP of A is `67.52.110.132`.<br>
  This results in a available IP-range of `67.52.110.129 - 67.52.110.142`.


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 5

<details>
  <summary>show</summary>

  ![Level 5](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_5.png)<br>
  Here we first come by the mighty routing table.<br>
  R1 has a fixed IP of `80.103.79.126` and a fixed mask of `255.255.255.128`, which results in a mask of `255.255.255.128` and an IP-range of `80.103.79.1 - 80.103.79.125` for A1.


  Now to conquer the routing table of A it is as easy as setting the **destination** as `default` or `0.0.0.0/0` and the destination has to be the IP of the directly connected router R1, `80.103.79.126`.<br>


  Same concept applies to connecting B to the R2.


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 6

<details>
  <summary>show</summary>

  ![Level 6](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_6.png)<br>
  This level introduces us to the Internet.<br>
  We again start with looking at the fixed IP-addresses and masks.


  IP of A1 is fixed and mask of R1, which A1 is connected to through the switch, is fixed as well.<br>
  So we need to match those in order for them to be in the same network.<br>
  Mask for this network will be `255.255.255.128` which then will result in 2 subnets.<br>
  Combined with the fixed IP of `29.65.6.227` one subnet will be from `29.65.6.1` to `29.65.6.126` and the other <br>`29.65.6.129 - 29.65.6.254`.<br>
  In order for R1 and A1 to be in the same network, the possible address-range of R1 will be `29.65.6.129 - 29.65.6.254`.


  Now set the routing table of A in order to reach R1.


  The **destination** of the routing table of the internet needs to be set to the network address of the R1-A1 network, which in this case is `29.65.6.128`, combined with the CIDR of the network, which is `/25`.<br>
  This results in a **next hop** of `29.65.6.128/25`.


  **Destination** of the routing table of the router can be set to `default` or `0.0.0.0/0`.


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 7

<details>
  <summary>show</summary>

  ![Level 7](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_7.png)<br>
  Level 7 is pretty straight forward and not too complicated, you just need to make sure that no networks overlap with each other.


  First goal will be to find an appropriate mask to use.<br>
  Since we will need 3 different subnets, by looking into the [table](https://github.com/tblaase/Net_Practice#masks) you will be able to decide which mask will be required.<br>
  I did choose `255.255.255.252` or in CIDR `/30` as my mask because it provides me with subnets, each having 2 usable IP-addresses.<br>
  Now you just need to fill in all the correct IP's in order to create the 3 networks:


  - A1 R11 (network range of `107.198.14.0 - 107.198.14.3`)
  - R12 R21 (network range of `107.198.14.252 - 107.198.14.255`)
  - R22 C1 (i did choose a network range of `107.198.14.4 - 107.198.14.7`)


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 8

<details>
  <summary>show</summary>

  ![Level 8](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_8.png)<br>
  Level 8 now will be a little tricky because you really need to be aware of overlapping networks.


  First thing we can solve is the connection of R13 and R21.<br>
  The routing table of R2 gives you the fixed IP of R13 as `141.195.172.62` and as this network only consists of 2 needed IP-addresses we can set the mask of R13 and R21 to `255.255.255.252` in order to make business with overlapping IP-addresses easier.<br>
  This will then result in `141.195.172.61` as the address of R21.<br>


  In R12 we see the fixed IP, which is `163.166.250.12`, so this needs to be put into the routing table of the Internet.<br>


  Now to set up the connection of D1 and R23.<br>
  First, set the mask of R23, since the mask of D1 is fixed to `255.255.255.240`.<br>
  Then put in 2 IP-addresses which are part of the same network intoR23 and D1, i decided to use the lowest subnet of the mask, since it is a not used IP-range yet, which is `141.195.172.1 - 141.195.172.14`.<br>
  So IP of R23 will be `141.195.172.1` and of D1 will be `141.195.172.2`.<br>


  For the network between R22 and C1 we are free to choose any mask we want. In order to make it as easy as possible i set it to `255.255.255.252`, because i only need 2 usable IP-addresses. After that i then choose a free range for my IP's.<br>
  In this case i did chose the next free one after the network of R23 and D1, which will be `141.195.172.17 - 141.195.172.18`.<br>


  Last thing to do is to set all the routing tables accordingly.<br>
  For C and D it's easy, both use `default` or `0.0.0.0/0` as a **destination** and the IP of the Interface of R2 they are directly connected to as **next hop**.<br>

  For the routing table of R1 it is a little harder.<br>
  Even though it would, for Net_Practice, work to just set the **destination** to `default` and get away with it just working, there is no way this should work as easy as this.<br>
  Because that would result in the routing table having 2 default destinations which lead to a different **next hop**, which if you think about doesn't make any sense, because the router would have no way of knowing which default to use.


  To make it more sensible, the destination needs to be set to a value that leads to R2 and can go either way, to D1 and to C1.<br>
  Because we used the lowest two IP-ranges for the two target networks, that need to be reached, the **destination** will be `141.195.172.0/27` the IP adress is of the network, that we want to reach and the CIDR will just define that the first 27 bits of the IP have to be `141.195.172`, so it will be able to communicate with IP's ranging from `141.195.172.0` to `141.195.172.255`.


  [back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 9

<details>
  <summary>show</summary>

  ![Level 9](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_9.png)<br>
  In Level 9 we encounter another weakness of the project. The router is not doing any IP-translation when a computer reaches out to the internet.<br>
  This can be seen by trying to connect C to the internet.


  First we set the ,mask of R22 and C1 to `255.255.255.252`, in order to block as little IP's as possible.<br>
  Now you have to decide on which IP-range to use for this network. I decided for the top-end, with the usable IP-addresses beeing `10.0.0.253` and `10.0.0.0.254`.<br>
  Now set the **next hop** in the routing table of C to the IP of R22.<br>
  Now change the routing table of R1, R2 and the Internet to make it work, as you learned before.


  If you now hiy the `check again` button, it will show you `Goal 6 : cation need to communicate with Internet - Status : KO - No reverse way, try again ...` for this demonstration we will just ignore all of the other goals.<br>
  Now you can see at the small red box at the bottom right corner:

  ```
  ******* Goal ID 6 ********
  forward way : C -> I (163.172.250.1)
  on C : packet accepted
  on C : destination does not match any interface. pass through routing table
  on C : route match 0.0.0.0/0
  on C : send to gateway 10.0.0.254 through interface C1
  on R2 : packet accepted
  on R2 : destination does not match any interface. pass through routing table
  on R2 : route match 0.0.0.0/0
  on R2 : send to gateway 50.165.17.254 through interface R21
  on R1 : packet accepted
  on R1 : send to R12
  on I : packet accepted
  on I : destination reached
  reverse way : I -> C (10.0.0.253)
  on I : packet accepted
  private subnets not routed over internet
  ```

  From this we can see, the package from C reaches the Internet, but since the router only attached the private IP of C1 without translating it to a public IP, the Internet can't send any package back to a private IP.<br>


  All we have to do now to make it work, is to change every apperance of our `10.0.0.x` address to `9.0.0.x`.<br>
  Once you have done that you are greeted with <br>`Goal 6 : cation need to communicate with Internet - Status : OK - Congratulations !!`


  So, for Net_Practice, a network can't have any IP which is part of a private Network, as soon as it will need connection to the Internet.


  Now, all that is left is to solve the remaining 5 Goals.


  3 Goals will be solved by creating the A-B-R11 network first, then connecting it to the Internet.<br>
  First, the mask of R11 is fixed, so set the same for B1 and A1.<br>
  Second, this network can not use private IP-addresses, so get rid of them.<br>
  Third, set the routing tables of A and B so they can reach R11.<br>
  Fourth, set the network address combined with the mask as a **destination** in the routing table of the internet.<br>
  In my case this was `106.198.154.0/25`.<br>


  The last two goals are depending on D to work.<br>
  As you can see in the routing table of D, the **next hop** is fixed, so put the same IP into R23.<br>
  The **destination** can be set to `default` or `0.0.0.0/0`.<br>
  Since the mask of that network is fixed as well, set it accordingly.


  Now, if we didn't forget anything, all that should be left, is to fix the routing table of R1.<br>
  For this you need the network-address of the R23-D1 network.<br>
  You can find this with the same logic, as before by just extending the [table](https://github.com/tblaase/Net_Practice#masks) above.<br>
  With this you will be able to find out that the mask `/18` divides our IP-range into 4 subnets:


  - `63.239.0.0 - 63.239.63.255`
  - `63.239.64.0 - 63.239.127.255`
  - `63.239.128.0 - 63.239.191.255`
  - `63.239.192.0 - 63.239.255.255`


Our fixed IP is part of `63.239.64.0 - 63.239.127.255`, so the network-address is `63.239.64.0`, combine this with our mask of `/18` and you have the missing **destinaton** of our routing table, `63.239.64.0/18`.


[back to contents](https://github.com/tblaase/Net_Practice#contents)

</details>

### Level 10

<details>
  <summary>show</summary>


  ![Level 10](https://github.com/tblaase/Net_Practice/blob/main/my_solutions/Level_10.png)

  The easiest part will be the connection of H2 and H1 in their network.<br>
  The mask of this network is fixed by R11, set the masks of H21 and H11 accordingly.<br>
  Set the IP of H21 to match the rest of the network, it can be in the range of `158.103.36.3 - 158.103.36.126`.<br>

  Now we are setting up the H41-R23 network and its connection to the Internet.<br>
  The mask is fixed, so set it accordingly.<br>
  The IP of R23 is fixed by the routing table of H4, so set it to the correct one.<br>
  Now go along the route connecting it to the Internet, you will notice the mask of R21 is fixed so set the mask of R13 accordingly.<br>
  The routing table of R1 already has the default set, as a connection to the internet.<br>
  So now the package should be able to reach the Internet and only thing to fix is the routing table of the Internet.<br>
  For this to be correct we only need to change the CIDR of the **destination**, so it is able to communicate with all `158.103.36.x` addresses.<br>
  This is done by changing the CIDR to `/24`, so it can reach `158.103.36.0 - 158.103.36.255`.<br>


  The hardest part of this level will now be the setup of the R22-H31 network and the correct setup of the routing table of R1.<br>
  First, set the mask of R22 and H31 to `255.255.255.252` since we only need 2 usable IP-addresses and this creates the least problems with overlapping ip-ranges.<br>
  Second, you need an IP-range that is still free. For this, we will take a look at all of the other networks.<br>


  - `150.152.40.0 - 150.152.40.127` is taken by R11-H21-H11
  - `150.152.40.128 - 150.152.40.191` is taken by R23-H41
  - `150.152.40.252 - 150.152.40.255` is taken by R13-R21


  So my decision was to take the next free part after `150.152.40.128 - 150.152.40.191`, which with the `/30` mask will be `150.152.40.192 - 150.152.40.195`.<br>
  Set the addresses accordingly to the usable ones of the range, you decided on.<br>


  Lastly, for the routing table of R1 we need the network-address of the R22-H31 network, which in my case is `150.152.40.192/` and it's mask, which is `/30`, set the **destination** accordingly.<br>

</details>


[back to contents](https://github.com/tblaase/Net_Practice#contents)
