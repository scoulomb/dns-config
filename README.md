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

### Prerequisites

In https://github.com/scoulomb/scoulomb.github.io/settings, custom domain is `coulombel.it`.
We should also enforce https.

### Example of resolution 

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

If pointing to github directly 
www 300 IN CNAME coulombel.it. -> scoulomb.github.io.
we come back to https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md#resolution-flow,

<!-- working as did that before,
also replaced sylvain.coulombel.site by this example as we need to use indirection for this due to github page constraints , but DNS config would work -->


Note we do not re-process the tree to resolve `coulombel.it`, for resolution details, as a consequence it the same process as here:
https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/1-real-own-dns-resolution-example.md.
Where we add a supplementary `CNAME` indirection.

<!-- site and it the same, com had seen little difference yes confirm OK -->


### Redirection (coulombel.it but site similar)

When using redirection it points to Gandi redirection webserver.
Which then redirect following same DNS process.

For instance check `CNAME` `cv.coulombel.it` in [it zone file](it/fwd.coulombel.it.db). 
````shell script

[13:53][master]⚡ ~/dev/dns-config
➤ curl cv.coulombel.it | grep title                                                                                                                                           vagrant@archlinux
[...]
<title>301 Moved Permanently</title>
curl -L cv.coulombel.it --ouptut out.pdf
# ensure DNS update (proxy etc...)
````

DNS redirection server will then resolve (http://scoulomb.github.io/resume.pdf).
Note referring to domain itself works. 

````shell script
http://sysy.coulombel.it PERMANENT http://coulombel.it
sysy	CNAME	10800	webredir.vip.gandi.net.
````

Here it would resolve coulombel.it

<!-- Actually not related to https://worldtechit.com/gtm-vs-ltm-difference-f5-global-local-traffic-manager/ -->

### http vs https

Github enforces http -> https when usng DNS.
From: https://docs.github.com/en/github/working-with-github-pages/securing-your-github-pages-site-with-https
> You can enforce HTTPS for your GitHub Pages site to transparently redirect all HTTP requests to HTTPS.

This is what we do.

Thus when doing redirection outbound can be http it will be translated to https.
Cleaner to set https.
But if inbound only http, https will not work this is why we define the 2 (http+https). 


### Dry run 

- http://coulombel.it
- http://www.coulombel.it
- http://sylvain.coulombel.it
- http://cv.coulombel.it
- https://coulombel.it
- https://www.coulombel.it
- https://sylvain.coulombel.it
- https://cv.coulombel.it

-> redirection need some time to be setup

## Site configuration

### Config

Zone file is [here](./site/fwd.coulombel.site.db).


It is similar to it.

### Dry-run

- http://coulombel.site
- http://sylvain.coulombel.site
- https://coulombel.site
- https://sylvain.coulombel.site


Initially not but not due to DNS cache but redirection server cache because of old redirections (+ maybe old dns entries)
Since creating

````shell script
http://test.coulombel.site PERMANENT http://scoulomb.github.io 
And entry
test	CNAME	10800	webredir.vip.gandi.net.
````

is working directly.

## Notes 

- Page compliant with https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md (ok updated)
- Authoritative reverse zone registar: https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/2-modify-tld-ns-record.md#note-about-reverse-zone =>OK (updated)
- gist alignment and official doc (same pattern as the appendix ): https://gist.github.com/matt-bailey/bbbc181d5234c618e4dfe0642ad80297 => OK
- resolution flow: see [example of resolution](#Example-of-resolution) =>OK.
- cache: https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/3-dns-propagation-effect.md (ok updated)
=> if proxy issue change machine => OK




