---
title: Selecting a Website Monitoring Tool
date: '2016-10-03 00:00:00'
published: true
layout: post
summary: In need of a server monitoring solution...
categories: monitoring pingdom newrelic nodeping
---
## Pingdom:

### Positives:

* mobile app
* large number of testing locations
* 10 checks at the yearly price is reasonably priced.
* Built-in “PageDuty”-lite incident response is handy, though overkill for personal web servers.
* I like the root cause analysis any time a check fails. Provides full connection output, response headers, etc. Extremely helpful when troubleshooting the cause of the failed check.

### Negatives:

* New website design is painfully slow and confusing.
* Can’t add a new check via the mobile app
* No option to specify host headers for a check — such as specify IP and specify the hostname directly.
* No public status page unless you pay 2x per month.
 

## NodePing:

### Positives:

* Free public status page
* Website is fast and clean, though lacking some features
* Pricing is attractive, even without a yearly agreement.

### Negatives:

* No mobile app
* Relatively few testing locations
* No option to specify host headers for a check — such as specify IP and specify the hostname directly.
* Virtually nothing in the way of detail when a check fails. Also no easy way to go back and find a failed check after 300 successful checks have passed.
 

They both have a variety of checks — HTTP/HTTPS, UDP/TCP arbitrary port check, POP/SMTP/IMAP, and DNS checks. Both send me an email and push notification via Pushover whenever there’s an issue. Both use 1 minute checks, and confirmation from 3 locations before an alert is triggered.

I like StatusCake, but their checks seem spotty at best. They report all kinds of intermittent downtime when every other monitoring service sees zero issues. Not exactly great when your server monitoring tool is lying to you.

I also tested Monitus and CopperEgg. Didn’t like either one. I use New Relic’s free plan which is handy, also Linode’s Longview tool with the free plan.

Ultimately it looks like I’ll be going with Pingdom, even though it’s not my favourite choice.