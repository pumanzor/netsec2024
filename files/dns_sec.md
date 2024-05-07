
## Seguridad en DNS


* The Internet was small
* fewer than 100 hosts
* Everybody knew everybody else
* Centralised: host file distributed to everyone
* But it didn’t scale

### Historia...

* ARPANET utilized a central file HOSTS.TXT
* Contains names to addresses mapping
* Maintained by SRI’s NIC (Stanford-Research-Institute: Network-Information-Center)
* Administrators email changes to NIC
* NIC updates HOSTS.TXT periodically
* Administrators FTP (download) HOSTS.TXT

* As the system grew, HOSTS.TXT had problems with:
* Scalability (traffic and load)
* Name collisions
* Consistency


***

*The “Domain Name System” Created in 1983 by Paul Mockapetris (RFCs 1034 and 1035), modified, updated, and enhanced by a mayriad of subsequent RFCs

* What Internet users use to reference anything by name on the Internet
* The mechanism by which Internet software translates names to addresses and vice versa


### What is DNS ?

* Domain Name System
* RFC1035
* Distributed database
* Translation
    name -> IP address
    IP address -> name

DNS es una base de datos dinámica, escalable, jerárquica y distribuida globalmente que proporciona una asignación entre nombres de host, direcciones IP (IPv4 e IPv6), registros de texto, información de intercambio de correo (registros MX), información del servidor de nombres (registros NS) y seguridad de información con claves definida en los resource records (RR). 

La información definida en los RR se agrupa en zonas y se mantiene localmente en un servidor DNS para que pueda ser recuperada globalmente a través de la arquitectura DNS distribuida. 

DNS puede usar ya sea el Protocolo de datagramas de usuario (UDP) o el Protocolo de control de transmisión (TCP) e históricamente utiliza un puerto de destino de 53.

* System to convert names to IP addresses:

    www.uchile.cl      ----> 200.89.76.16

* Reverse DNS:

    16.76.89.200.in-addr.arpa   ----> www.uchile.cl.

* DNS

* Case insensitive
* Transport is either UDP or TCP on port 53
* Indexed by “domain names”
* A “domain name” is a sequence of labels
    - www.mit.edu
    - emi.ac.ma


![dns1](https://github.com/pumanzor/netsec/blob/master/imgs/domain-name-space.gif)



* DNS administration shared
* No single central entity administers all data
* Delegation = distribution of administration


### DNS is a Database

* Contains different types of data:
* IP Addresses
* Where to send email
* Who is responsible
* Geographical info
* etc..





![dnst1](https://github.com/pumanzor/netsec/blob/master/imgs/dnst1.png)




### Como funciona DNS
![](https://github.com/pumanzor/netsec/blob/master/imgs/dnst3.png)



***



### Ejemplo de una DNS query

![](https://github.com/pumanzor/netsec/blob/master/imgs/dnst3.png)


***


![](https://github.com/pumanzor/netsec/blob/master/imgs/dnst4.png)


***


### Recursion is Important

No single machine can have all the information in the world

-----

![root1](https://github.com/pumanzor/netsec/blob/master/imgs/stub1.png)

-----

![root1](https://github.com/pumanzor/netsec/blob/master/imgs/stub2.png)

-------

![root1](https://github.com/pumanzor/netsec/blob/master/imgs/stub3.png)

----

![root1](https://github.com/pumanzor/netsec/blob/master/imgs/rootservers.png)

--------
![root1](https://github.com/pumanzor/netsec/blob/master/imgs/rootwiki.png)

-----
En Chile

![root1](https://github.com/pumanzor/netsec/blob/master/imgs/espejosroot.png)

------
![a](https://github.com/pumanzor/netsec/blob/master/imgs/tld.png)

------

### Delegation Record for .COM
(Generic top-level domain)

### Sponsoring Organisation
  VeriSign Global Registry Services
  

    HOST NAME	               IP ADDRESS(ES)
    a.gtld-servers.net	192.5.6.30     2001:503:a83e:0:0:0:2:30
    b.gtld-servers.net	192.33.14.30   2001:503:231d:0:0:0:2:30
    c.gtld-servers.net	192.26.92.30   2001:503:83eb:0:0:0:0:30
    d.gtld-servers.net	192.31.80.30   2001:500:856e:0:0:0:0:30 
    e.gtld-servers.net	192.12.94.30   2001:502:1ca1:0:0:0:0:30
    f.gtld-servers.net	192.35.51.30   2001:503:d414:0:0:0:0:30
    g.gtld-servers.net	192.42.93.30   2001:503:eea3:0:0:0:0:30
    h.gtld-servers.net	192.54.112.30  2001:502:8cc:0:0:0:0:30
    i.gtld-servers.net	192.43.172.30  2001:503:39c1:0:0:0:0:30
    j.gtld-servers.net	192.48.79.30   2001:502:7094:0:0:0:0:30
    k.gtld-servers.net	192.52.178.30  2001:503:d2d:0:0:0:0:30
    l.gtld-servers.net	192.41.162.30  2001:500:d937:0:0:0:0:30
    m.gtld-servers.net	192.55.83.30   2001:501:b1f9:0:0:0:0:30

------------------
### Delegation Record for .CL
(Country-code top-level domain)

ccTLD Manager
NIC Chile (University of Chile)
Miraflores 222, Piso 14
Santiago RM 832-0198
Chile

------------------
    HOST NAME	                 IP ADDRESS(ES)

    a.nic.cl	                190.124.27.10     2001:1398:121:0:190:124:27:10 
    b.nic.cl	                200.7.4.7         2001:1398:274:0:200:7:4:7
    c.nic.cl	                200.16.112.16 
    cl-ns.anycast.pch.net	204.61.216.30     2001:500:14:6030:ad:0:0:1
    cl1.dnsnode.net	        194.146.106.34    2001:67c:1010:8:0:0:0:53
    sns-pb.isc.org	        192.5.4.1         2001:500:2e:0:0:0:0:1

------
Ejemplo resolucion .net

![q](https://github.com/pumanzor/netsec/blob/master/imgs/typical-dns-resolution-8.gif)

--------
DNS Query

![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnsquery1.png)

-----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnsquery2.png)

-----


![a](https://github.com/pumanzor/netsec/blob/master/imgs/nsrecord.png)

------

![a](https://github.com/pumanzor/netsec/blob/master/imgs/arecord.png)

-----


![a](https://github.com/pumanzor/netsec/blob/master/imgs/aaaarecord.png)

-----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/cname.png)

-----


![a](https://github.com/pumanzor/netsec/blob/master/imgs/mxrecord.png)

-----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/soa.png)
---

![a](https://github.com/pumanzor/netsec/blob/master/imgs/soa2.png)

------

![a](https://github.com/pumanzor/netsec/blob/master/imgs/autoritative.png)

-----
![a](https://github.com/pumanzor/netsec/blob/master/imgs/cachevsauth.png)

------


![a](https://github.com/pumanzor/netsec/blob/master/imgs/ttl.png)

-----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnsvul2.png)

-----
![a](https://github.com/pumanzor/netsec/blob/master/imgs/dns-query-packet.gif)

------
![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnswire1.png)
-----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnswire2.png)
----

![a](https://github.com/pumanzor/netsec/blob/master/imgs/dnswire3.png)
-----

### Instalar BIND9  :+1: 

    apt-get install bind9

### Archivos de configuracion

     /etc/bind/

    drwxr-sr-x   2 root bind  4096 mar 27 14:34 .
    drwxr-xr-x 144 root root 12288 mar 27 23:07 ..
    -rw-r--r--   1 root root  3923 ago 28  2017 bind.keys
    -rw-r--r--   1 root root   237 ago 28  2017 db.0
    -rw-r--r--   1 root root   271 ago 28  2017 db.127
    -rw-r--r--   1 root root   237 ago 28  2017 db.255
    -rw-r--r--   1 root root   353 ago 28  2017 db.empty
    -rw-r--r--   1 root root   270 ago 28  2017 db.local
    -rw-r--r--   1 root root  3171 ago 28  2017 db.root
    -rw-r--r--   1 root bind   463 ago 28  2017 named.conf
    -rw-r--r--   1 root bind   490 ago 28  2017 named.conf.default-zones
    -rw-r--r--   1 root bind   165 ago 28  2017 named.conf.local
    -rw-r--r--   1 root bind   904 mar 27 14:34 named.conf.options
    -rw-r-----   1 bind bind    77 mar  6 21:21 rndc.key
    -rw-r--r--   1 root root  1317 ago 28  2017 zones.rfc1918



