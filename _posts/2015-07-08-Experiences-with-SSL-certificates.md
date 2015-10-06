---
layout: post
title: "Experiences with SSL certificates"
---

Some time ago I discovered that the SSL certificate on a Rails system I maintain was about to expire. The expiration date was actually set to the middle of my vacation, so I decided I had to act or all the users would be getting security warnings.

Now the last time, and the first, I had anything to do with SSL certificates, was during the heartbleed days. Back then I requested a re-issue of the certificate of the aforementioned system. I have also enabled SSL on this site for the admin functions through a strange, but useful option given by my web host. I am truly amazed of how complicated the certificate world is, but I’ve learned a lot lately, so let me share some of it here.

##Certificates usually come with a price##

There aren’t many exceptions for this rule. Some providers of certificates give you free certificates for a limited period, e.g. 30 days, but unless you need it only for that amount of time, you’ll have to pay. There are some small exceptions though. StartSSL has an offer that sounds good, under certain conditions you can get the certificate for free, for one year at a time. This is great e.g. if you’re developing a system hosted at Amazon AWS and need a secure connection during the development phase. Another model I’ve seen, is that web hosting companies offers SSL as an option you can turn on in their control panel with one click. At one.com this is a free and optional function included our web hotel. Look for that when choosing a traditional web host.

##Test your setup: HTTPS ain’t just HTTPS##

I earlier thought that HTTPS was one single standard protocol with handshake and encryption in one standardized package, if there was HTTPS, all was well. It turns out it’s not that simple. The are a bunch of settings, ciphers, protocols, server features, etc. that you need to be aware of to maximize security. Of course there is, security needs to evolve, get stronger. Bugs needs to be cleaned out. However, changing standards of HTTPS is no easy task. The server part is easy, install the latest software, and set it up with tight security. There are tons of guides on that, but that doesn’t really help if the browser connecting cannot use the latest TLS version for example. So, you need to allow only what you need. To get an idea on what you need to do with your server, I recommend using the SSL test from SSL Labs. SSL Labs also have a browser tester. You want to get a grade A+ when testing your server, although that isn’t always doable to be honest.

##Installation is a hassle##

Unless you go for the one click SSL I found at one.com, getting and installing a certificate correctly is a hassle. I would have liked it to be a simple feature you turn on, but since you have to manage the private key somehow, that will not suffice in many cases. You cannot do it all in one go, because you have to generate the certificate request and private key first. Then you need to send the request to the certificate issuer, and depending on which type of certificate you need, you have to go through a more or less demanding approval process. This is good, the approval and verification is the very trust you buy!

However, things are improving slowly. Especially on the hosting side of things. Just think about how easy it is to install new certificates in a load balancer listener on Amazon AWS. After getting the certificate, all you have to do is enter the certificate, the private key and certificate chain, and all servers managed by that load balancer will use the certificate (as long as you access the servers through the load balancer, and not directly through their public DNS name). And as I mentioned, web hosts are starting to create simpler solutions.

##Run your own server if you need total privacy##

I’ve been thinking a lot about this. You keep your private key secret, but still have to put it on your web server, usually hosted by people you don’t know. I can only speculate in how tempting these private keys must be for government agencies. At the end of the day, HTTPS security on a server running at some hosting company is great for securing your private information from abuse by criminals, like your banking activities. However to protect against government agencies, I wouldn’t trust it to do much more than delay their decryption. You need to physically run your server yourself to be sure that the private keys are not going anywhere near any agency. I don’t need this level of security, but I think it’s worth mentioning, as some people do need extreme security, and for very good reasons.

##It’s worth it!##

However, all in all, HTTPS is worth the hassle. Encrypting communication is usually a good thing, and an absolute must in many cases. With HTTPS on your site, you’re sure that nobody on the free public wireless is eavesdropping on your users at least. At least all forms and login pages should be encrypted. Please don’t use it against me that my site isn’t utilizing HTTPS yet though, I’m working on it, and I will share how I did it when I get there.
