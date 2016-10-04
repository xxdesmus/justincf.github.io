---
published: true
layout: post
title: How to Test if DANE is Properly Configured
date: 'Mon Oct 3 2016 13:20:00 GMT-0700 (PDT)'
summary: Here’s a simple way to check if DANE is properly setup on a site
categories: dane dnssec
---
Here's a simple way to check if [DANE](https://en.wikipedia.org/wiki/DNS-based_Authentication_of_Named_Entities) is properly setup on a site:

    # echo -n | openssl s_client -connect spdysync.com:443 | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' | openssl x509 -noout -fingerprint -sha256 | tr -d :
    depth=2 /C=IL/O=StartCom Ltd./OU=Secure Digital Certificate Signing/CN=StartCom Certification Authority
    verify error:num=19:self signed certificate in certificate chain
    verify return:0
    DONE
    SHA256 Fingerprint=461479314CDEC67FB609C812EB74737BAA5327455AD422BA606C88DD530BF2C2

And then compare that value against published TLSA record:

    # dig +short TLSA _443._tcp.spdysync.com
    3 0 1 461479314CDEC67FB609C812EB74737BAA5327455AD422BA606C88DD 530BF2C2

These value should match. If they don't assume the site has been compromised.

This assumes of course the domain is also signed with [DNSSEC](https://en.wikipedia.org/wiki/Domain_Name_System_Security_Extensions).
