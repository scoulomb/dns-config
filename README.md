# DNS config

## Purpose

This repo contains DNS config of domain I own.
In particular for my website  [scoulomb.github.io](scoulomb.github.io) hosted as github [page](https://github.com/scoulomb/scoulomb.github.io).

It is based on observation made in [github page and DNS](https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md).

And some learning from https://github.com/scoulomb/myDNS

Note I flipped the role of `coulombel.it` and `coulombel.site`, as I will release `coulombel.site`.

## Initial Requirements

## Config

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

## Prerequisites

In https://github.com/scoulomb/scoulomb.github.io/settings, custom domain is `coulombel.it`.
We should also enforce https.

## Example of resolution 

````shell script
➤ nslookup -type=A sylvain.coulombel.it                                                                                                                                       vagrant@archlinuxServer:         10.0.2.3
Address:        10.0.2.3#53

Non-authoritative answer:
sylvain.coulombel.it    canonical name = coulombel.it.
Name:   coulombel.it
Address: 217.70.184.38
Name:   coulombel.it
Address: 185.199.111.153
Name:   coulombel.it
Address: 185.199.109.153
Name:   coulombel.it
Address: 185.199.108.153
Name:   coulombel.it
Address: 185.199.110.153

➤ dig sylvain.coulombel.it @8.8.8.8 +additional +trace                   vagrant@archlinux
; <<>> DiG 9.16.0 <<>> sylvain.coulombel.it @8.8.8.8 +additional +trace
;; global options: +cmd
.                       86386   IN      NS      a.root-servers.net.
.                       86386   IN      NS      b.root-servers.net.
.                       86386   IN      NS      c.root-servers.net.
.                       86386   IN      NS      d.root-servers.net.
.                       86386   IN      NS      e.root-servers.net.
.                       86386   IN      NS      f.root-servers.net.
.                       86386   IN      NS      g.root-servers.net.
.                       86386   IN      NS      h.root-servers.net.
.                       86386   IN      NS      i.root-servers.net.
.                       86386   IN      NS      j.root-servers.net.
.                       86386   IN      NS      k.root-servers.net.
.                       86386   IN      NS      l.root-servers.net.
.                       86386   IN      NS      m.root-servers.net.
.                       86386   IN      RRSIG   NS 8 0 518400 20200905050000 20200823040000 46594 . Dq91VGzGqOe/3UZcsf9X9ZmAjQpM7y8jFvzuMg7I8jxSv2DT/oI6synk vK1bMVEmdhBaCTY4nCiWUqsgskpxbRu9xFUKu+TDj18/XgrrARv5HkrH dGtFj9+B7HNxHq/9AMDdYarVtRxlKy2OQVKaTLzOLQJLnLhhN6KCAnKd iX7y0Cy9tPqoTrCvryWeB12BjTAxaZ/GYhstrHYlMv6SdJw6C9de29Cn RCfMpCgaLXv0yquT26NkoRz5PHroh5lzqRNPpDkQ62e6QA6C/kpc9hZz E2JqYric7c1giFZzZ+W25Y1Hb1GYUd0JPGDC6/7e0vbvmhWd3qDFTZR8 lkRPjg==;; Received 525 bytes from 8.8.8.8#53(8.8.8.8) in 40 ms

it.                     172800  IN      NS      a.dns.it.
it.                     172800  IN      NS      m.dns.it.
it.                     172800  IN      NS      r.dns.it.
it.                     172800  IN      NS      s.dns.it.
it.                     172800  IN      NS      dns.nic.it.
it.                     172800  IN      NS      nameserver.cnr.it.
it.                     86400   IN      DS      41901 10 2 47F7F7BA21E48591F6172EED13E35B66B93AD9F2880FC9BADA64F68C E28EBB90
it.                     86400   IN      RRSIG   DS 8 1 86400 20200905050000 20200823040000 46594 . dBB+khsPC3+E0AUERCliFVa1p5OIah9syUOa9PJqzsXDJzarDOSgLeJE 9+QBvI9LoTMr5vzyZqu1jBTRLpJ2wsre33b/7Zj1iaMakV4fJY6+3bK3 MZwATRtHKHJPvXOPikDYKLxJAImCHHvhjZ4HlwTyaEFKnYg+7slCdrP8 PxXFclh1lgYG7CjA7atB3HR+tScOqO4Za1ZHq6D7JVyj3ujnCuWhoH9f lSv9Bj1IXOQ+YWA5dIxQtEeezL9jRXL/SdFuscvJnOGtdkC7/fGooNli j9ivluOxM9MfVE4+spaWWCdSoki70dnyedJOIgWUL7we6QdYBEHN2Fv4 2N8kMQ==
;; Received 767 bytes from 198.41.0.4#53(a.root-servers.net) in 53 ms

coulombel.it.           10800   IN      NS      ns-142-b.gandi.net.
coulombel.it.           10800   IN      NS      ns-161-a.gandi.net.
coulombel.it.           10800   IN      NS      ns-142-c.gandi.net.
GFIBE36K070MA38B1S83H1953NGJK3FP.it. 3600 IN NSEC3 1 1 10 A4FF6100C383BF18 GFJVB6V2HKROQNC3AADEN7DAQE3E7DB7 NS SOA RRSIG DNSKEY NSEC3PARAM
GFIBE36K070MA38B1S83H1953NGJK3FP.it. 3600 IN RRSIG NSEC3 10 2 3600 20200922100323 20200823100323 18395 it. DdqKJwyVpccAJBWPd4YB+Jc67bjMwsnr6IRDEc3pUsWMC3w9NmSA0NoQ yLXDRJrgZ3i7lKk7WXhstxDgWToEUhQoQ5Q8hNKG+ZD42+dXKGrBUIY2 F/xVS3TfzBeiU2NKBaYTJ2YckDkl5VDPume6lUtJsHRqWh99skGRWhZD VFSP0MR/tc67BZ/K21vmfTYrQLkxYCGsX8z5dQS1/JQdLXYcMV+JLvyI WNHBOPGarE+K3oNNi+GT0w7AY5n7lRG9PN487gVWxcXJJBID8hiTAkBB p+gV6mYLIT1hRqhK8Tc2Xe2OZ5lxHUs44gVwmH3n45elzx3rYrz803/E wAqyAw==
OOH7LT9LOFCDS0CLK3E1RKFBORIQ6MGM.it. 3600 IN NSEC3 1 1 10 A4FF6100C383BF18 OOJ4BB5SF0FU1U7F59BMSPDB7OU6ILT1 NS DS RRSIG
OOH7LT9LOFCDS0CLK3E1RKFBORIQ6MGM.it. 3600 IN RRSIG NSEC3 10 2 3600 20200922100323 20200823100323 18395 it. dH6786p7n1piWf6m7qadBznIUrngVzE9b1NkBPJf6ADJs25jRhN8nAsV 67/oSEl47DUK22o+OB1KPergf948EfoITSoxrFj7xStCkovC0nbGuzDD 2PymZO7jKrOnIat+BRIp/v9tp7Z+Q/MBdRK4xEXZPOSmGfpzGJqImFTa KFKCMRMkQ8yxBF3/3wNBhvUmpqZ0mAvVVrp/cYgWg37GgWZUZfynlIur Lp+z2Zm45PkfxWnHqtY67Tgf5hC9/u+MvSIvanY8KwtI5vKNsqX1dbNJ 8eKp4+MNHU8Q5gkEJ98JXxcSvAajeZNE61dFsp2LSnqbNMWfALsYO1fY H5NQtg==
;; Received 912 bytes from 194.146.106.30#53(s.dns.it) in 56 ms

coulombel.it.           10800   IN      A       185.199.110.153
sylvain.coulombel.it.   300     IN      CNAME   coulombel.it.
coulombel.it.           10800   IN      A       217.70.184.38
coulombel.it.           10800   IN      A       185.199.111.153
coulombel.it.           10800   IN      A       185.199.108.153
coulombel.it.           10800   IN      A       185.199.109.153
;; Received 143 bytes from 217.70.187.143#53(ns-142-c.gandi.net) in 46 ms
````


This case mix the resolution flow of subdomain configuration and APEX
https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md

DNS resolution flow is: 
- `sylvain.coulombel.it` ->
-`DNS server` (autho is Gandi) ->
- redirect to `coulombel.it` ->
- `DNS server` (autho is Gandi) ->
- redirect to github IP ->
- github uses CNAME file to determine which github page to serve (similar to vhost, OpenShift route, K8s Ingress controller)

If pointing to github directly 
sylvain 300 IN CNAME coulombel.it. -> scoulomb.github.io.
we come back to https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md#resolution-flow,

Note we do not re-process the tree to resolve `coulombel.it`, for resolution details, as a consequence it the same process as here:
https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/1-real-own-dns-resolution-example.md.
Where we add a supplementary `CNAME` indirection.

<!-- site and it the same, com had seen little difference yes confirm OK -->

When using redirection it points to Gandi redirection webserver.

## Notes 

- Page compliant with https://github.com/scoulomb/github-page-helm-deployer/blob/master/appendix-github-page-and-dns.md (ok updated)
- Authortiative reverse : https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/2-modify-tld-ns-record.md#note-about-reverse-zone =>OK (updated)
- gist alignment and official doc (same pattern as the appendix ): https://gist.github.com/matt-bailey/bbbc181d5234c618e4dfe0642ad80297 => OK
- resolution flow: see [example of resolution](#Example-of-resolution) =>OK.
If using redirection.
We use `CNAME` to redirect to gandi: 
````shell script

[13:53][master]⚡ ~/dev/dns-config
➤ curl cv.coulombel.it | grep title                                                                                                                                           vagrant@archlinux
[...]
<title>301 Moved Permanently</title>
curl -L cv.coulombel.it --ouptut out.pdf
# ensure DNS update (proxy etc...)
````
<!-- Actually not related to https://worldtechit.com/gtm-vs-ltm-difference-f5-global-local-traffic-manager/ -->

Then it reuses normal resoution.

- cache: https://github.com/scoulomb/myDNS/blob/master/2-advanced-bind/5-real-own-dns-application/3-dns-propagation-effect.md (ok updated)
=> if proxy issue change machine => OK
- coulombel.site and sylvain.coulombel.site not working 

````shell script
http://coulombel.site PERMANENT http://scoulomb.github.io
http://sylvain.coulombel.site PERMANENT http://scoulomb.github.io
````

Given the config for IT domain I would expect we can do

`PERMANENT http://(sylvain.)coulombel.it` 

for both cases (not tried and more Gandi specific).

but not due to DNS cache but redirection server cache because of old redirections (+ maybe old dns entries)
Since creating

````shell script
http://test.coulombel.site PERMANENT http://scoulomb.github.io 
And entry
test	CNAME	10800	webredir.vip.gandi.net.
````

is working directly.

DNS config aligned with repo, waiting some time => 

I also enforced https at github level so I expect that even if direction are http we are routed to https.
From: https://docs.github.com/en/github/working-with-github-pages/securing-your-github-pages-site-with-https
> You can enforce HTTPS for your GitHub Pages site to transparently redirect all HTTP requests to HTTPS.

Confirm it is correct =>