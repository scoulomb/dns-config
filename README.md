# DNS config

## Purpose

This repo contains DNS config of domain I own.
In particular for my website  [scoulomb.github.io](scoulomb.github.io) hosted as github [page](https://github.com/scoulomb/scoulomb.github.io).

It is based on observation made in [github page and DNS](https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md).

And some learning from https://github.com/scoulomb/myDNS

Note I flipped the role of `coulombel.it` and `coulombel.site`, as I will release `coulombel.site`.

## Initial Requirements

### it domain

Following names 
- `coulombel.it`
- `www.coulombel.it`
- `sylvain.coulombel.it`
to point to my webpage `scoulomb.github.io`

`cv.coulombel.it` to point to  `scoulomb.github.io/resume.pdf`.

### Site domain

- `coulombel.site` to point to  `coulombel.it` <=> `scoulomb.github.io` here
- `sylvain.coulombel.site` to point to `coulombel.it` <=> `scoulomb.github.io` here

And all should work in http and https.

## it configuration 

### Config 

Zone file is [here](./it/fwd.coulombel.it.db).
We can follow instruction inside.
Note generated TTL is 10800 I set to 300.

### Example of resolution

www.coulombel.it case

<details>
<summary>Details...</summary>
<p>


#### If we have: www 300 IN CNAME coulombel.it.

````shell script
➤ nslookup -type=A www.coulombel.it 8.8.8.8                                                                                                                                   vagrant@archlinux
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
www.coulombel.it        canonical name = coulombel.it.
Name:   coulombel.it
Address: 217.70.184.38
Name:   coulombel.it
Address: 185.199.110.153
Name:   coulombel.it
Address: 185.199.109.153
Name:   coulombel.it
Address: 185.199.108.153
Name:   coulombel.it
Address: 185.199.111.153

[14:39][master]⚡ ~/dev/dns-config
➤ dig www.coulombel.it @8.8.8.8 +additional +trace                                                                                                                            vagrant@archlinux

; <<>> DiG 9.16.0 <<>> www.coulombel.it @8.8.8.8 +additional +trace
;; global options: +cmd
.                       81687   IN      NS      h.root-servers.net.
.                       81687   IN      NS      g.root-servers.net.
.                       81687   IN      NS      d.root-servers.net.
.                       81687   IN      NS      e.root-servers.net.
.                       81687   IN      NS      b.root-servers.net.
.                       81687   IN      NS      c.root-servers.net.
.                       81687   IN      NS      f.root-servers.net.
.                       81687   IN      NS      m.root-servers.net.
.                       81687   IN      NS      j.root-servers.net.
.                       81687   IN      NS      k.root-servers.net.
.                       81687   IN      NS      a.root-servers.net.
.                       81687   IN      NS      i.root-servers.net.
.                       81687   IN      NS      l.root-servers.net.
.                       81687   IN      RRSIG   NS 8 0 518400 20200905050000 20200823040000 46594 . Dq91VGzGqOe/3UZcsf9X9ZmAjQpM7y8jFvzuMg7I8jxSv2DT/oI6synk vK1bMVEmdhBaCTY4nCiWUqsgskpxbRu9xFUKu+TDj18/XgrrARv5HkrH dGtFj9+B7HNxHq/9AMDdYarVtRxlKy2OQVKaTLzOLQJLnLhhN6KCAnKd iX7y0Cy9tPqoTrCvryWeB12BjTAxaZ/GYhstrHYlMv6SdJw6C9de29Cn RCfMpCgaLXv0yquT26NkoRz5PHroh5lzqRNPpDkQ62e6QA6C/kpc9hZz E2JqYric7c1giFZzZ+W25Y1Hb1GYUd0JPGDC6/7e0vbvmhWd3qDFTZR8 lkRPjg==
;; Received 525 bytes from 8.8.8.8#53(8.8.8.8) in 40 ms

it.                     172800  IN      NS      r.dns.it.
it.                     172800  IN      NS      s.dns.it.
it.                     172800  IN      NS      nameserver.cnr.it.
it.                     172800  IN      NS      dns.nic.it.
it.                     172800  IN      NS      a.dns.it.
it.                     172800  IN      NS      m.dns.it.
it.                     86400   IN      DS      41901 10 2 47F7F7BA21E48591F6172EED13E35B66B93AD9F2880FC9BADA64F68C E28EBB90
it.                     86400   IN      RRSIG   DS 8 1 86400 20200905050000 20200823040000 46594 . dBB+khsPC3+E0AUERCliFVa1p5OIah9syUOa9PJqzsXDJzarDOSgLeJE 9+QBvI9LoTMr5vzyZqu1jBTRLpJ2wsre33b/7Zj1iaMakV4fJY6+3bK3 MZwATRtHKHJPvXOPikDYKLxJAImCHHvhjZ4HlwTyaEFKnYg+7slCdrP8 PxXFclh1lgYG7CjA7atB3HR+tScOqO4Za1ZHq6D7JVyj3ujnCuWhoH9f lSv9Bj1IXOQ+YWA5dIxQtEeezL9jRXL/SdFuscvJnOGtdkC7/fGooNli j9ivluOxM9MfVE4+spaWWCdSoki70dnyedJOIgWUL7we6QdYBEHN2Fv4 2N8kMQ==
;; Received 791 bytes from 192.112.36.4#53(g.root-servers.net) in 143 ms

coulombel.it.           10800   IN      NS      ns-142-b.gandi.net.
coulombel.it.           10800   IN      NS      ns-142-c.gandi.net.
coulombel.it.           10800   IN      NS      ns-161-a.gandi.net.
L05G1LKNU8D42GAS5JQB182UISAAHT8E.it. 3600 IN NSEC3 1 1 10 4E65CB475F4378AA L05N1JFMO0SPMG3TVCSKU3TS027898VJ NS SOA RRSIG DNSKEY NSEC3PARAM
L05G1LKNU8D42GAS5JQB182UISAAHT8E.it. 3600 IN RRSIG NSEC3 10 2 3600 20200922130309 20200823130309 18395 it. WEGDjIA8357iVpfGHqWYBvClSwmfLPZYRL+9Q/S6v9b4IbBUkEypDoq4 Aq2T221aoWYCbKiWe4pfL27CIwsJ1jJjnTjOvRM1VcGahzPoKDrE/ygc mh/eujhYPeaBvmlo9V2a2Oy4+DwRtmLtJQ4XBAfMm5x8Lh7MUGvnKAs4 4MHW6dd51IseyZXRX0cRtd7elghORVRN1aBVbidaouVEzxKcnGmbFkvN DNrZ43yey7SqSIwJE4E8QFioswJbS5FLzqyr7TgWo7AVXF67htWvL15D Z5PoLZYbwwPpOHbUoVgt6OKg1QYM1s1UCo3Hq6u+zFALjT/MaAHFFWdg Upp2Tg==
MIIUIQ9985OAVAA9GV1KCN3U775V1UHK.it. 3600 IN NSEC3 1 1 10 4E65CB475F4378AA MIPG8M6H8L5PV0H4JARM9L8VLNB27O9E NS DS RRSIG
MIIUIQ9985OAVAA9GV1KCN3U775V1UHK.it. 3600 IN RRSIG NSEC3 10 2 3600 20200922130309 20200823130309 18395 it. J3x0ARzNGVsrmr3HmaRsqA8A6vB2F3XYDv13sKYiD8BFV05xjROYYwsh U3pNP/um55mLRA0ees4P35ja+6Rjhn6jfiaEtZ9wpLs+gLWLjnfb0gSi t0xMfgE6dzEY89HS9vrZteehjym/+SYhewx9egLw2+sLmPZIh/iVeq42 I+LUcvfz8VZtkLW8oe08iKYVJgUh675fl9yQ4WtQo4gHNoAMpIrZg2mX 4N946p6YubvBlfWaDsSSSvO3lVMXPMfYL3jg9K9rNoVWjXWH5MuVnZFh oYh49AIn83hTIiuK4XSevZeUfotJeBf0Uq8cOQLw+z4Sqa+D70QrWUc/ 3Ey5/A==
;; Received 906 bytes from 194.0.16.215#53(a.dns.it) in 56 ms

coulombel.it.           10800   IN      A       185.199.110.153
coulombel.it.           10800   IN      A       185.199.109.153
coulombel.it.           10800   IN      A       185.199.111.153
coulombel.it.           10800   IN      A       185.199.108.153
coulombel.it.           10800   IN      A       217.70.184.38
www.coulombel.it.       300     IN      CNAME   coulombel.it.
;; Received 139 bytes from 217.70.187.143#53(ns-142-c.gandi.net) in 43 ms
                                                                                                                                                                     vagrant@archlinux
````


This case mix the resolution flow of subdomain configuration and APEX (particular case of `www`)
https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md


DNS resolution flow is: 
- `www.coulombel.it` ->
-`DNS server` (autho is Gandi) ->
- redirect to `coulombel.it` ->
- `DNS server` (autho is Gandi) ->
- redirect to github IP ->
- github uses CNAME file to determine which github page to serve (similar to vhost, OpenShift route, K8s Ingress controller)

Note we do not re-process the tree to resolve `coulombel.it`, for resolution details.
As a consequence it the same process as [APEX A record](https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md#a-records).
And here https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/1-real-own-dns-resolution-example.md.
Where we add a supplementary `CNAME` internal indirection.


#### Case www 300 IN CNAME scoulomb.github.io.

````shell script
➤ nslookup -type=A www.coulombel.it 8.8.8.8                                                                                                                                   vagrant@archlinux
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
www.coulombel.it        canonical name = scoulomb.github.io.
Name:   scoulomb.github.io
Address: 185.199.108.153
Name:   scoulomb.github.io
Address: 185.199.109.153
Name:   scoulomb.github.io
Address: 185.199.110.153
Name:   scoulomb.github.io
Address: 185.199.111.153


➤ dig www.coulombel.it @8.8.8.8 +additional +trace                                                                                                                            vagrant@archlinux

; <<>> DiG 9.16.0 <<>> www.coulombel.it @8.8.8.8 +additional +trace
;; global options: +cmd
.                       86266   IN      NS      c.root-servers.net.
.                       86266   IN      NS      j.root-servers.net.
.                       86266   IN      NS      h.root-servers.net.
.                       86266   IN      NS      l.root-servers.net.
.                       86266   IN      NS      b.root-servers.net.
.                       86266   IN      NS      i.root-servers.net.
.                       86266   IN      NS      f.root-servers.net.
.                       86266   IN      NS      m.root-servers.net.
.                       86266   IN      NS      d.root-servers.net.
.                       86266   IN      NS      k.root-servers.net.
.                       86266   IN      NS      a.root-servers.net.
.                       86266   IN      NS      e.root-servers.net.
.                       86266   IN      NS      g.root-servers.net.
.                       86266   IN      RRSIG   NS 8 0 518400 20200905170000 20200823160000 46594 . ZLSCECaB3Gaz7z7pJHvbwliu7KoWawuilyF+o+a2NlKBmI/n01XHUhAO u5SEYgtkAOUpTlboJNwWjkIFgmGcRjGlyRmCR7Pw61AGcu1vwNFoWAV3 Q4rBKgzELyyeWhFo49zE8a+a2m7huwqzy/fazQJR+iwgrHWDVppjz6Kc RSRBUq0R3Kgne0bzXINNU9h9OeNqb5OROIO00RCPBBc8J0do9trcM7PS L8DlImJiO98S/YMlpfashj9cqrUi5JI+Wm+8UF79B5MosILkqaBCjNXl cvPi/xYsxV6wD1H82tbrUxVSGUHTpxaYQhC2NxxZOUpLklkqrDb9vWm9 WagCow==
;; Received 525 bytes from 8.8.8.8#53(8.8.8.8) in 40 ms

it.                     172800  IN      NS      a.dns.it.
it.                     172800  IN      NS      m.dns.it.
it.                     172800  IN      NS      r.dns.it.
it.                     172800  IN      NS      s.dns.it.
it.                     172800  IN      NS      dns.nic.it.
it.                     172800  IN      NS      nameserver.cnr.it.
it.                     86400   IN      DS      41901 10 2 47F7F7BA21E48591F6172EED13E35B66B93AD9F2880FC9BADA64F68C E28EBB90
it.                     86400   IN      RRSIG   DS 8 1 86400 20200905170000 20200823160000 46594 . pQ5HFE+ylhNif4n99FPvIsYrO/i/Aq/jG3JBVPGxgoD2EjE9M2s0UTd1 wScCSrDr9nEV26azusHfSHJ911rf/BTbrIN7IGZE+mCfTUl7CIWOg9As cbKCx2yVZEwcT+6jOKJrzZcCFm9ha0NPGvCurJxGtrSL3QItsZOXOQ9v /X1iSzsqkb3uxUepe2VsUDvHHq4RR0gviuHm7wTW+gEx6HCCeBAV48+y 2k2XSWR+2twNtUiVwZodlhQZGrX+Cd8A4v3sZyVBltbHTNk6soc8xww4 I+ZyoVmS4hKo5bKp9HmndDlkLrRKLaU7VmpTn9F/frVVxC7F/Cb3el9r ZpjxXg==
;; Received 763 bytes from 199.7.83.42#53(l.root-servers.net) in 96 ms

coulombel.it.           10800   IN      NS      ns-161-a.gandi.net.
coulombel.it.           10800   IN      NS      ns-142-c.gandi.net.
coulombel.it.           10800   IN      NS      ns-142-b.gandi.net.
38F65J1IUIK3G5I3TCIT6261H9RT1N18.it. 3600 IN NSEC3 1 1 10 94DEC7DACE1F4539 38GACQ3C4SOKVHBIQD8F8DEFF1JSD6UK NS SOA RRSIG DNSKEY NSEC3PARAM
38F65J1IUIK3G5I3TCIT6261H9RT1N18.it. 3600 IN RRSIG NSEC3 10 2 3600 20200923000329 20200824000329 18395 it. ZxjanXzHuEW5Rr5UkHI3nvf63KFh4OFu4gezq4/ET2w7wO2P4OB0KQw3 ls6yCztPhpxp7IsaDWDyJEvT3n7IRDbwVbfjxjuKV57BYpO8bWVhJfqb Ioe31f3zmFgw9O7CnRGtrxamodhKmRQo0GFonOHllVSNxHAzKouRttva V5BRIBu8qZ9rIvioi5qqGf5u2B3P7287Q0wPFxh8IsXEPgy6QlzTBscD 2rpDv6FiVohlMPY91eZNZueltyG1yOTLqKAZVjsZcVDgTCLtkwvfISST dDLy6oM7nKC/uYooQk93ZIMcO/tkXSpJP0PhH4o1rnXEaJ5blesmeutZ t6gk3A==
6F0HQF0MISM65DSRLPQ3TKP3PH4SPQ0H.it. 3600 IN NSEC3 1 1 10 94DEC7DACE1F4539 6F2J1N0TE2CLT7Q6H1JDJ7MB7D5UIM7J NS DS RRSIG
6F0HQF0MISM65DSRLPQ3TKP3PH4SPQ0H.it. 3600 IN RRSIG NSEC3 10 2 3600 20200923000329 20200824000329 18395 it. NUNMOEUfdojgPSgro5kwFZfmb9vOrgaotZPeEmucVwqUPXA07GMo+YWC Xns6amd2u6paihZJFSWwHH/cDKAk1ueI0ApNlxp6S/QhiyCvumTvz3wT NvJXNQcLGs+1UwKj0JKTH8fS03wW5r5pKzMsxce1zcXAckrZrixd3CO5 ENBhCJhr6EKNMfSPegJivp6UoyJXTE6mZIguuPJQzosQOcJFJhwrrtNe QMHuHkRxFos8Qz8SSX6s3Gt158XBGJ6nTj4o+k3JdZci0iNuSvxwAhr/ VytPLuZW0XEKrwBNpBn8Hq3iCHUy503H1S/l91HnH6Yt6GBsxK3+mBrf FOkWgA==
;; Received 908 bytes from 194.146.106.30#53(s.dns.it) in 56 ms

www.coulombel.it.       300     IN      CNAME   scoulomb.github.io.
;; Received 77 bytes from 217.70.187.143#53(ns-142-c.gandi.net) in 40 ms

````

For the resolution flow, we we come back exactly to [subdomain resolution flow](https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md#resolution-flow).

For the details  same process as here https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/1-real-own-dns-resolution-example.md.
Except we get CNAME (instead of A), and need to resolve it after (could also be detailled).

<!-- 
replaced sylvain.coulombel.site by this example as we need to use indirection for this due to github page constraints,
but DNS config would work -->

<!-- site and it the same, com had seen little difference yes confirm OK -->


#### Case www 300 IN CNAME webredir.gandi.net.

````shell script
➤ nslookup -type=A www.coulombel.it 8.8.8.8                                                                                                                                   vagrant@archlinux
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
www.coulombel.it        canonical name = webredir.gandi.net.
Name:   webredir.gandi.net
Address: 217.70.184.56

[10:44] ~
➤ dig www.coulombel.it @8.8.8.8 +additional +trace                                                                                                                            vagrant@archlinux

; <<>> DiG 9.16.0 <<>> www.coulombel.it @8.8.8.8 +additional +trace
;; global options: +cmd
.                       84378   IN      NS      m.root-servers.net.
.                       84378   IN      NS      b.root-servers.net.
.                       84378   IN      NS      c.root-servers.net.
.                       84378   IN      NS      d.root-servers.net.
.                       84378   IN      NS      e.root-servers.net.
.                       84378   IN      NS      f.root-servers.net.
.                       84378   IN      NS      g.root-servers.net.
.                       84378   IN      NS      h.root-servers.net.
.                       84378   IN      NS      a.root-servers.net.
.                       84378   IN      NS      i.root-servers.net.
.                       84378   IN      NS      j.root-servers.net.
.                       84378   IN      NS      k.root-servers.net.
.                       84378   IN      NS      l.root-servers.net.
.                       84378   IN      RRSIG   NS 8 0 518400 20200906050000 20200824040000 46594 . ekBVs0eBVNL97qe3Xim4ps+N9NQaQNcRjA7Y22cdkmVfhbYKYf7eYF+j tVvo8h5Fu1LkxsyBYkFk7G1g4vDq6WI8Pya/20UQpo2nHEuQskdV2W5E Qw6JioPbWeCuMbaBe8aN/kCX+ItZPsaEHmHuiUFRyyLNp1i6u7BYHL4C v7UJJI5pFArSEDc/6DoVTJiyulN2cSinK+riQNWAW9HzuqGDnMt9MNQJ B2xAmygkcS4jTuOnfW+/3b7fRPpZyHCcKHDHRULcFjwGSo45SW66O/bn S/RsxR4f3lqu9xShzDD+PO07NegouYYCjhyl94ZaiVZJIrHFMXpBraxs 5AokTw==
couldn't get address for 'm.root-servers.net': not found
;; Received 525 bytes from 8.8.8.8#53(8.8.8.8) in 36 ms

it.                     172800  IN      NS      nameserver.cnr.it.
it.                     172800  IN      NS      s.dns.it.
it.                     172800  IN      NS      a.dns.it.
it.                     172800  IN      NS      r.dns.it.
it.                     172800  IN      NS      m.dns.it.
it.                     172800  IN      NS      dns.nic.it.
it.                     86400   IN      DS      41901 10 2 47F7F7BA21E48591F6172EED13E35B66B93AD9F2880FC9BADA64F68C E28EBB90
it.                     86400   IN      RRSIG   DS 8 1 86400 20200906050000 20200824040000 46594 . s7kwhf2vu/Psqo2jYuPlDwzsx8KEUHN0vjjLQjp/2adHpQXaHoh7qSwF aHmf6SA5JRxdyr7u2CKRHNcgXawMtECjVwXiwujoZv3hxS0B8kWpki30 rsM05ifsHzR4QgZLwqKQv95dE1U61FcHhBxQT4xQeQG6AjwJsiZLXy/W jJx4wxJ1QvGciK84W96yYj1KlaRKu3vMEmtp2wlPRANPuqF5ly/jTQsf BSbpA4eQL6gZMVIjn1EcklumX+dEv6yIrZ+EDi+upYvu4tGxeVp4r8Bn DPm44C0m0tqIVLkQC8Jk4c4iLSzt2ZT9EtJ5Ap98hgzBH6lwFTjCBcKJ NeBXYQ==
;; Received 771 bytes from 193.0.14.129#53(k.root-servers.net) in 60 ms

coulombel.it.           10800   IN      NS      ns-142-b.gandi.net.
coulombel.it.           10800   IN      NS      ns-142-c.gandi.net.
coulombel.it.           10800   IN      NS      ns-161-a.gandi.net.
JKH11F1TSP6JVSGON05TI32RBPM7K8OK.it. 3600 IN NSEC3 1 1 10 87E9C507F17B8F57 JKJFE18F74F25F9HI0A9S6BK6ADII04T NS SOA RRSIG DNSKEY NSEC3PARAM
JKH11F1TSP6JVSGON05TI32RBPM7K8OK.it. 3600 IN RRSIG NSEC3 10 2 3600 20200923090307 20200824090307 18395 it. EgDJZWv/H8cAn0dfwggQlsuydsfXC6SVc3R9bdniK3UvZJBEHsu5HLsX bNdgARD/Ge1vBxZ+BE4IfCouzh+aiQ/um49W2/WfvQd41NoOIPRPDuuN WheoM9PstCS1TUhT3U5YsUalPJPjAkllay3W8tnkJ8EKqZnk3RCRu9tU BhwUbG1CJdI9sG+tHG8Q+W9TztVusXIs1v9/Qoofr4Xx74a7lKd8gjV3 TE22mYXMkv0KNDb2qjSeWcfNkuoD5CjrjxrS5WWtrUEkeKLWH6DBAhU0 uCqgMP7xb42zinurHcOrWVIzhu3cMSLv/pwM/yP323SmKFI2HT1lEWu8 rrPk5Q==
EBBKIVFMDS99QEHKFUDVU5OCE4FG333H.it. 3600 IN NSEC3 1 1 10 87E9C507F17B8F57 EBHRO9VGNVDHA51M9359KRDPPE2UIR60 NS DS RRSIG
EBBKIVFMDS99QEHKFUDVU5OCE4FG333H.it. 3600 IN RRSIG NSEC3 10 2 3600 20200923090307 20200824090307 18395 it. SPMcZ6/WGhwnGyvP+oQuy/DJllR95awza0uMo3kdPt1OL4zbN/SXuntu hsi2nQ8VAvmJozUYlb0UCR7fFeU80SNVxxl7FsP2XwFoyxus6UJ5kvgc yeMCSJirxWQ4g2QpqJzdNfchDt8sZFJMW3vgqH2vr8VwF/QyTHnIUi1F 27Cy0fND7ycqQUo3j3opiOqN81VkfvseRbFfVmGP8RYytE9Ov9BSbJYg ru4MxcBM0bEArk62goN6In/0pSWZDvvIDz2QbAMJr82eKWq5q0JD+57H icQPGm4pq2Vx7muiBKgWij7YSNkddQmh29rj76vJrVJRLWmdVF73MbHo DKs6uQ==
;; Received 906 bytes from 193.206.141.46#53(r.dns.it) in 63 ms

www.coulombel.it.       300     IN      CNAME   webredir.gandi.net.
;; Received 77 bytes from 217.70.187.143#53(ns-142-c.gandi.net) in 46 ms
                                                                                                                                                                          vagrant@archlinux
````


For the details  same process as here https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/1-real-own-dns-resolution-example.md.
Except we get CNAME redirection servver instead od A.

Then redirection server resolves coulombel.it or scoulomb.github.io

</p>
</details>

### Redirection details (coulombel.it but site similar)

When using redirection it points to Gandi redirection webserver.
Which then redirect following same DNS process.

For instance check `CNAME` `cv.coulombel.it` in [it zone file](it/fwd.coulombel.it.db). 

````shell script
➤ curl cv.coulombel.it -v                                                                                                                                                     vagrant@archlinux*   Trying 217.70.184.56:80...
* Connected to cv.coulombel.it (217.70.184.56) port 80 (#0)
> GET / HTTP/1.1
> Host: cv.coulombel.it
> User-Agent: curl/7.69.1
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 301 Moved Permanently
< content-length: 0
< location: https://scoulomb.github.io/resume.pdf
< Connection: Keep-Alive
< Date: Mon, 24 Aug 2020 10:52:29 GMT
<
* Connection #0 to host cv.coulombel.it left intact
[10:52] ~/dev
➤ curl -L cv.coulombel.it > ~/dev/cv_output.pdf                                                                                                                               vagrant@archlinux
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100   162  100   162    0     0    298      0 --:--:-- --:--:-- --:--:--   298
100 1223k  100 1223k    0     0   222k      0  0:00:05  0:00:05 --:--:--  263k
````
             
DNS redirection server will then resolve (http://scoulomb.github.io/resume.pdf).

Note referring to domain itself works (cf also www in zone [file](./it/fwd.coulombel.it.db))

````shell script
http://sysy.coulombel.it PERMANENT http://coulombel.it
sysy	CNAME	10800	webredir.vip.gandi.net.
````

Here it would resolve coulombel.it

<!-- Actually not related to https://worldtechit.com/gtm-vs-ltm-difference-f5-global-local-traffic-manager/ -->

### http vs https

Then [check sylvain.coulombel.it comment in zone file](it/fwd.coulombel.it.db). 

Note when created certificate are visible in left menu.
We can validate a SSL certificate by:
- adding a DNS CNAME entry (comodo) -> done automatically when using Gandi live DNS
- by email redirection (admin@<domain>)
- by file

The CNAME record can be removed after Domain control validation.
This is why we can re-upload DNS config stored here:

The need of certificate is explained [in this article](https://github.com/scoulomb/misc-notes/blob/master/tls/README.md).
<!--
certif understood (signature) and link seems ok)
-->

### Dry run 

Wait after configuration is applied (but also fix error). We wait for:
- DNS update (but this is usually not an issue aw we can change DNS, machine (proxy)) -> https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/3-dns-propagation-effect.md
- Redirection server update (but should be fast if CNAME is not changed, from https://docs.gandi.net/en/domain_names/faq/web_forwarding.html#web-forwarding-faq)
- Certificate provisioned (otherwise http and https not working as mentioned  in [zone file](it/fwd.coulombel.it.db). 


Names to check are:
- http://coulombel.it
- http://www.coulombel.it
- http://sylvain.coulombel.it
- http://cv.coulombel.it
- http://cv.sylvain.coulombel.it
- https://coulombel.it
- https://www.coulombel.it 
- https://sylvain.coulombel.it
- https://cv.coulombel.it
- https://cv.sylvain.coulombel.it

(Note port 80/443 has no impact here for redirection, there is a default port for a given protocol http->80, https->443, not the contrary so it makes sense)

<!--
Port stop there
-->

All dry run is OK

## Site configuration

### Config

Zone file is [here](./site/fwd.coulombel.site.db).


It is similar to it domain.

### Dry-run

(wait after configuration applied)

- http://coulombel.site
- http://sylvain.coulombel.site
- http://cv.coulombel.site
- https://coulombel.site
- https://sylvain.coulombel.site
- https://cv.coulombel.site

All dry run is OK

## Original URL
And obviously 

- http://scoulomb.github.io
- http://scoulomb.github.io/resume.pdf
- https://scoulomb.github.io
- https://scoulomb.github.io/resume.pdf

And as comment from it Zone file is [here](./it/fwd.coulombel.it.db) for `coulombel.it`.
Note all other entries being redirection, they are also covered by certificate of let's encrypt. (cf. www case where it was our solution to be https).
<!-- clear ok no more, let's encrypt OK -->

## Notes 

- Page compliant with https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md (ok updated)
- Authoritative reverse zone registar: https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/2-modify-tld-ns-record.md#note-about-reverse-zone =>OK (updated)
- gist alignment and official doc (same pattern as the appendix ): https://gist.github.com/matt-bailey/bbbc181d5234c618e4dfe0642ad80297 => OK
Except I explained why I used redirection for HTTPs
- resolution flow: see [example of resolution](#Example-of-resolution) =>OK.
- cache: https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/3-dns-propagation-effect.md (ok updated)
=> if proxy issue change machine => OK

<!-- reapply conf test
Conf reapplied -> OK for site and it. yes twice, and again (as aded comment doubt but yes and no impact anayway OK)
Wait and dry-run Test -> OKOK
-->

<!--
http://www.coulombel.it is secured
https://github.com/scoulomb/dns-config/blob/master/it/fwd.coulombel.it.db (see www.coulombel,it),
as explained in (sylvain.coulombel.it/ section - 1)
Not tested (because we have to stop) but if redirect to coulombel.it and not enforced https in coulombel.it I expect to have http.
-->