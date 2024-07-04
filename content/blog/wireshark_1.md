---
author: Ellisa Adams
title: Getting Started with Wireshark - Part 1
date: 2024-06-15
description: An intro for the uninitiated
tags: ["tech","Wireshark","pcap"]
thumbnail:
  url: img/wireshark_3/wireshark_thumbnail.jpg
  author: Google images
---

### “Wireshark isn’t nearly as scary as real sharks!”

#### Me, I said that

&nbsp;
#### WHAT IS WIRESHARK
Wireshark is a program that captures the traffic of computers and servers. It displays the information that is coming and going in packet form. However, if you are just starting out, it is important to understand how exactly this works. Before we can really get into Wireshark, you need to understand a little bit more about packets and IP addresses. This will be important for the information that I’ll be covering in the next post.

Let’s say you decide to mail a letter to your cousin. You haven’t spoken to your cousin in a while and your letter is pretty lengthy. To mediate this, USPS decides to instead mail your letter as three separate postcards (I know this wouldn’t actually happen, but just bear with me). Each postcard, in the world of Wireshark, would be a packet!

Each of your postcards (or packets) has part of the original letter, as well as the sender’s address, the receiver’s address, and a number indicating which postcard it is in the series of 3. These components would make up the contents and header.

As your postcards (or packets) make their journey towards your cousin, they pass through several USPS sorting stations. These would be networks

As your postcards (or packets) make their journey towards your cousin, they pass through several USPS sorting stations. These would be networks.

Unless, of course, you had something secret in your original letter. Perhaps it was a code to the vault of gold you keep in your basement! In this case, at one of the sorting hubs (or networks), your letter becomes encrypted before it continues along its merry way. Can’t be too safe!

That’s a VERY basic look at packets! A packet is simply an “envelope” of information with all of the address info needed to make its trip towards its destination.

&nbsp;

#### IP ADDRESSES

There is so much that could be said about the nuances of IP addresses, but we are just going to cover one concept for the purposes of this Wireshark blog series.

Let’s say you have one of those massive golf umbrellas that you use to keep you and your family dry on rainy days. You all stand under the umbrella together and are collectively using the umbrella. However, you and your family members continue to be individuals. 

IP addresses work in a similar fashion. One household may use a single IP address, but there could be any number of devices within that home that are collectively using that IP address. 

&nbsp;

#### WHAT DOES THIS HAVE TO DO WITH WIRESHARK?

Everything! Wireshark captures packets and their IP address information. By utilizing Wireshark, a user can see which IP addresses these packets of information are coming from and where it is that they are going. But before you can do all that, you have to download Wireshark.


#### DOWNLOADING WIRESHARK

This part is very straightforward. Just go to wireshark.org, click “get started,” and download the appropriate version of Wireshark for your computer. It’s totally free and super easy to do. Just follow the installation wizard prompts as they appear on the screen.

&nbsp;

#### CONCLUSION

See? Wireshark is much less scary than real sharks. In my next post, I’ll discuss how computers participate in TCP (Transmission Control Protocol), sending packets to and fro. In the third post in this series, I’ll guide you through filtering and analyzing all the traffic happening on your computer.  You’ll be able to see just how much information you are sending by simply having your computer on and running! 

&nbsp;



# 🦈