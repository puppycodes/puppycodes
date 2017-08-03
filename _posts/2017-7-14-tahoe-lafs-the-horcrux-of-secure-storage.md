---
layout: post
title: "Tahoe-LAFS, The Horcrux of Secure Storage"
description: "Tahoe LAFS stores a file by creating an encrypted copy of the data and splitting it into multiple pieces distributed across many servers. This concept is remarkably similar to a Horcrux from Harry Potter."
date: 2017-05-16
tags: ["storage", "crypto", "horcrux", "decentralized"]
draft: false
---
 [Tahoe-LAFS](https://tahoe-lafs.org/) is a secure and decentralized system for data storage and backups. Tahoe lends itself to a more developer focused community but it can be installed and used by anyone with the help of the new graphical interface called [Gridsync](https://github.com/gridsync/gridsync) created by Christopher R. Wood and sponsored by [Least Authority](https://leastauthority.com/) & [UX Fund](https://usable.tools/uxfund.html) .

##### How does it work?

Tahoe LAFS stores a file by creating an encrypted copy of the data and splitting it into multiple pieces distributed across many servers. This concept is remarkably similar to a Horcrux from Harry Potter.

##### Horcrux

 _A Horcrux is an object in which a Dark wizard or witch has hidden a fragment of his or her soul for the purpose of attaining immortality.[1] Horcruxes can only be created after committing murder, the supreme act of evil._

 Luckily! We don't have to murder anyone 😅 to leverage this concept. Using the Horcrux as an example I will attempt to explain how Tahoe works...

 ![horcrux](/assets/images/horcrux.jpg)


![horcrux](/assets/images/voldemort.png)

##### So what just happened?

First we start with Voldemorts soul... aka: the data you want to backup. Next we encrypt the data and smash it into a little bits. The encrypted pieces of data are then distributed across multiple servers or in our example several horcrux 🤓... To get the data back.. we re-glue the pieces back together using decryption keys, and now we are looking at your backup!



##### Provider-independent security

Why is this good or better than traditional methods? It's important to ask if you want your to be in control of your data. When security and/or storage is handled by a large corporation... sometimes that corporation can be influenced by government pressure or monetary interests and that might not pan out well depending what your goals are. Every time you quickly click through that lil privacy agreement theres a possibility they changed something. Wouldn't it be nicer if you didn't have to read it at all?
Here's the more technical graph from Tahoe-LAFS:

![horcrux](/assets/images/technical-tahoe.jpg)


Only the individual with the original link otherwise known as FURL, will be able to access the data. This means that there is no possibility of a government or third party being able to access your data without the link!

Version 0.1 of Gridsync was just released today and I will be testing it out soon!
