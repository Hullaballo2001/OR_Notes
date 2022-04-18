---
title: "Quête 0 : Adressage IP - Ressources"
date: 2021-11-14
categories:
  - AIS
tags:
  - AIS
  - Adressage
  - CIDR
toc: true
toc_label: "Contents"
toc_icon : "columns"
toc_sticky: true
---

# Ressources

|     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- |
| Classe | IP  | leading bits | default mask<br>net id bits/host id bits | length of netmask | nb of networks | nb of hosts |
| A   | <ins>0</ins>.0.0.1 - 9. 255.255.255<br>**10.0.0.0 - 10.255.255.255** = privées<br>11.0.0.0 - 126.255.255.255<br><ins>127</ins>.0.0.0 - 127.255.255.255 = localhost | 0xxx | **255.0.0.0**<br>1 segment utilisé<br>8 “1” / 24 "0"<br>CIDR **/8** | 8<br>nb de bits à 1 | 126<br>2<sup>8-1</sup> \- 2 | 16 777 214<br>2<sup>24</sup> -2 |
| B   | <ins>128</ins>.0.0.0 - 172.15.255.255<br>**172.16.0.0  172.31.255.255** = privées<br>172.32.0.0 - <ins>191</ins>.255.255.255 | 10xx | **255.255.0.0**<br>2 segments utilisés<br>16 “1” / 16 "0"<br>CIDR **/16** | 16<br>nb de bits à 1 | 16 382<br>2<sup>16-2</sup> \- 2 | 65 534<br>2<sup>16</sup> \- 2 |
| C   | <ins>192</ins>.0.0.0 - 192.167.255.255<br>**192.168.0.0 - 192.168.255.255** = privées<br>192.169.0.0 - <ins>223</ins>.255.255.255 | 110x | **255.255.255.0**<br>3 segments utilisés<br>24 “1” / 8 "0"<br>CIDR **/24** | 24<br>nb de bits à 1 | 2 097 150<br>2<sup>24-3</sup> \- 2 | 254<br>2<sup>8</sup> \- 2 |
| D   | 224.0.0.0 - 239.255.255.255 (multicast) | 1110 |     |     |     |     |
| E   | 240.0.0.0 - 254.255.255.255 (research) | 1111 |     |     |     |     |

## Formules :
\- pour avoir le nombre de réseaux : 2<sup>(netmask length - nb used segments)</sup> \- 2  (.0 pour l’adresse réseau et .255 pour l’adresse de broadcast)

\- pour avoir le nombre d’hôtes par réseau : 2<sup>(nb de zéros du masque)</sup> \- 2 (idem sauf pour /31 et /32 où il n’y en a qu’une des deux ou zéro)

![7933f0aa79b7e5bbbac94ae007e24eee](https://user-images.githubusercontent.com/87373259/163793766-a6c881ac-2ba9-4a20-9f93-814f8f2ac67c.png)

**255.255.255.255** [broadcasts] to all hosts on the local network.

https://www.computerhope.com/jargon/i/ip.htm

![cabd9495c052ed701a8638221bcc5163](https://user-images.githubusercontent.com/87373259/163793805-7d81bc8f-f2fc-4093-94dd-85da11cacc52.png)


Comme montré par le tableau précédent, le masque de réseau est déterminé par le nombre de bits pour le réseau selon la classe de l’adresse.

Quant au masque de sous-réseau, il permet de subdiviser la partie machine en sous-réseau et machine. Il doit donc posséder les bits du masque de réseau à 1 en plus de ceux du sous-réseau.

Exemples de subdivision possible des 8 bits machine pour un réseau 192.168.0.0 (classe C, masque réseau 255.255.255.0, 24 bits) :

- masque de sous-réseau 255.255.255.0 : 0 bits de sous-réseau et 8 bits pour la machine, (car 0 = 00000000
- masque de sous-réseau 255.255.255.192 : 2 bits de sous-réseau et 6 bits pour la machine, (car 192 = 11000000)
- masque de sous-réseau 255.255.255.240 : 4 bits de sous-réseau et 4 bits pour la machine (car 240 = 11110000)

On observe donc que c’est le masque qui détermine le nombre de machines d’un réseau. Ainsi, on verra par la suite qu’on choisira le masque en fonction du nombre de machines que l’on veut installer.

### Adresses réseaux et adresses de diffusion

Une adresse réseau est une adresse IP qui désigne un réseau et non pas une machine de ce réseau. Elle est obtenue en plaçant tous les bits de la partie machine à zéro.

Une adresse de diffusion (« broadcast » en anglais) est une adresse permettant de désigner toutes les machines d’un réseau, elle est obtenue en plaçant tous les bits de la partie machine à un.

Par exemple :
|     |     |     |     |
| --- | --- | --- | --- |
| IP (classe) | masque | adresse réseau | adresse de diffusion |
| 10.10.10.10 (A) | 255.0.0.0 | 10.0.0.0 | 10.255.255.255 |
| 192.168.150.35 (C ) | 255.255.255.0 | 192.168.150.0 | 192.168.150.255 |

[https://fr.wikibooks.org/wiki/R%C3%A9seaux\_TCP/IP/Adressage\_IP_v4](https://fr.wikibooks.org/wiki/R%C3%A9seaux_TCP/IP/Adressage_IP_v4)

### Quelles adresses pour les masques de sous-réseau ?

Etant donné que l’on conserve la contiguïté des bits, on va toujours rencontrer les mêmes nombres pour les octets du masque. Ce sont les suivants :

11111111 11111110 11111100 … 10000000 00000000  Soit en décimal : 255, 254, 252, 248, 240, 224, 192, 128, et 0.

Ainsi, on peut tout de suite dire si un masque semble valide au premier coup d’oeil. Un masque en 255.255.224.0 sera correct alors qu’un masque en 255.255.232.0 ne le sera pas (à moins de ne pas vouloir respecter la contiguïté des bits)

Vous pouvez aller voir tous les masques possibles dans la RFC suivante: [RFC 1878](http://www.frameip.com/rfc-1878-variable-length-subnet-table-for-ipv4/)

### CIDR

Une autre notation est souvent utilisée pour représenter les masques. On la rencontre souvent car elle est plus rapide à écrire. Dans celle-ci, on note directement le nombre de bits significatifs en décimal, en considérant que la contiguïté est respectée. Ainsi, pour notre exemple 192.168.25.0/255.255.255.0, on peut aussi écrire 192.168.25.0/24, car 24 bits sont significatifs de la partie réseau de l’adresse.

De même, les écritures suivantes sont équivalentes :

10.0.0.0/255.0.0.0 = 10.0.0.0/8

192.168.25.32/255.255.255.248 = 192.168.25.32/29 (car 248 = 11111000 donc 5 “1” à ajouter aux 24)

### Comment choisir le bon masque : en fonction du nombre de machines

Etant donné que le masque détermine le nombre de machines qu’il pourra y avoir sur un réseau, c’est souvent de cette information que l’on part pour choisir le masque. Etant donné que l’on travaille en binaire, le nombre de machines possible au sein d’un réseau sera une puissance de 2. Pour un nombre donné de machines, il faudra donc choisir la puissance de 2 immédiatement supérieure pour pouvoir adresser les machines. De plus, il faudra prévoir un certain nombre d’adresses supplémentaires pour accueillir de nouvelles machines.

Ainsi, disons que l’on possède le réseau 193.225.34.0/255.255.255.0 et que l’on veut faire un réseau de 60 machines au sein de celui-ci. On veut 60 machines, il faut ajouter deux adresses pour le réseau et le broadcast, ce qui fait 62 adresses au total. La puissance de 2 supérieure à 62 est 64, mais cela ne nous laisserait que 2 adresses pour évoluer, ce qui est un peu juste. On préfèrera donc un réseau de 128 adresses. Pour identifier 128 adresses, il nous faut 7 bits (128 = 2^7) Donc dans notre masque, 7 bits seront à 0 pour identifier la partie machine, et les 25 bits restants seront à 1. Ce qui donne :

11111111.11111111.11111111.10000000 et en décimal : 255.255.255.128

### Comment déterminer la plage d’adresses à partir du masque et d’une adresse ?

Nous avons vu précédemment que le masque devait être associé à une adresse IP pour avoir une valeur. Le choix de la plage d’adresses sur laquelle il s’applique est donc tout aussi important !! Nous avons choisi un masque qui nous permettra d’identifier 128 machines. Mais nous possédons une plage de 256 adresses. Où faut-il placer nos 128 adresses dans cette plage ? Peut-on les placer n’importe où ?

La réponse est bien sûr non. Nous n’avons que deux possibilités pour choisir notre plage, les adresses de 0 à 127, et les adresses de 128 à 255. Choisir une plage de 32 à 160 serait une erreur, et le réseau ne fonctionnerait pas.

Voici l’explication:

La différenciation du réseau va se faire sur le premier bit du dernier octet (vu que nos trois premiers octets sont fixés à 193.225.34) Si ce bit est à 0, cela correspond aux adresses de 0 à 127. S’il est à 1, cela correspond aux adresses de 128 à 255. Ainsi, si l’on choisit une plage d’adresses de 32 à 160, les adresses de 32 à 127 auront le premier bit de leur dernier octet à 0, alors que les adresses de 128 à 160 auront ce même bit à 1, elles seront alors considérées comme étant dans deux réseaux différents !!!

Ainsi, quel que soit le nombre de machines à placer dans une plage, on ne peut pas choisir l’adressage n’importe comment.

PS: Dans notre cas, les deux choix possibles sont identiques, mais l’on verra par la suite que ce n’est pas toujours le cas pour des plages plus petites…

### Une méthode simple pour trouver les adresses de réseau possible

Il n’est pas toujours évident de savoir si une adresse correspond bien à celle d’un réseau selon le masque que l’on a choisi. Avec la méthode suivante, vous devriez pouvoir vous en sortir. Il faut avant tout que vous ayez déterminé le masque de sous-réseau selon le nombre de machines dont vous avez besoin. Ensuite, selon l’octet significatif (qui n’est pas à 0 ou 255) faites 256-cet_octet=X. L’adresse de réseau devra alors être un multiple de X. Un petit exemple pour être un peu plus clair. On veut par exemple 50 machines, on choisit donc un masque en 255.255.255.192. C’est le dernier octet qui est significatif, on fait donc 256-192=64. Il faut donc que le dernier octet de l’adresse de réseau soit un multiple de 64. Si on prend la plage 10.0.0.0/255.255.255.0, on pourra choisir les adresses de réseau suivantes :

10.0.0.0, 10.0.0.64, 10.0.0.128, 10.0.0.192.

Penser à rester dans les ip privées :

10.0.0.0/255.0.0.0 soit plus de 16 millions d’adresses

192.168.0.0/255.255.0.0 soit près de 65000 adresses

172.16.0.0/255.240.0.0 soit plus d’un million d’adresses

[https://www.frameip.com/masques-de-sous-reseau/#21-8211-lrsquoidentification-des-machines](https://www.frameip.com/masques-de-sous-reseau/#21-8211-lrsquoidentification-des-machines "Cours sous réseaux ***")    Cours sous réseaux ***

Pour compter en binaire :
|     |     |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2<sup>10</sup> | 2<sup>9</sup> | 2<sup>8</sup> | 2<sup>7</sup> | 2<sup>6</sup> | 2<sup>5</sup> | 2<sup>4</sup> | 2<sup>3</sup> | 2<sup>2</sup> | 2<sup>1</sup> | 2<sup>0</sup> |
| 1024 | 512 | 256 | 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
|     |     |     |     | 1   | 0   | 0   | 0   | 0   | 0   | 0   |
