---
author: Ellisa Adams
title: Getting Started with Wireshark - Part 2
date: 2024-05-31
description: Let’s talk about polite conversations. 
tags: ["tech","Wireshark", "Pcap"]
thumbnail:
  url: img/wireshark_3/wireshark_thumbnail.jpg
  author: Google images
---

### “Etiquette mean behaving yourself a little better than is absolutely essential”

#### Will Cuppy

&nbsp;

#### THREE WAY HANDSHAKE - Establishing the connection

Your computer is constantly having conversations with other network devices, servers, and maybe even streaming platforms. However, as your computer does this, it is following a strict code of conversational decorum called TCP (Transmission Control Protocol).

Basically, this is what happens when your computer initiates TCP (or “talks to”) another device:

As in real life, it starts with a handshake. Your computer, we’ll call it Computer 1, sends a SYN (Synchronize) packet to another device, let’s say it’s a computer called Computer 2. In doing this, Computer 1 is basically saying, “Hello! I’d like to talk to you!”

The handshake isn’t over yet, though! Computer 2 responds with a SYN-ACK (Synchronize-Acknowledge) packet. This packet is essentially Computer 2’s way of saying, “Why yes! I would love to talk!”

At last, Computer 1 sends an ACK (Acknowledge) packet back to computer 2. Which is really just Computer 1’s way of confirming, “Okay, we are now having a conversation!”

This process is called the three-way handshake because of the three steps taken for the handshake to be completed. It can be summed up like this:

&nbsp;

1. Computer 1 sends a SYN packet to Computer 2
2. Computer 2 sends a SYN-ACK packet to Computer 1
3. Computer 1 sends an ACK packet to Computer 2

&nbsp;

#### A GRACIOUS GOODBYE - Closing the connection

Computer 1 and Computer 2 have a delightful time sending packets back and forth. However, all conversations eventually come to an end. This is true in the human world and in the computer world. Once again though, your computer is incredibly considerate and ends the conversation with grace and tact. After all, wouldn’t it be odd if you were having a conversation with someone and then simply turned and walked away? You wouldn’t do that, and neither would your computer!

In keeping with their penchant for politeness, computers bid one another adieu with yet another handshake. This time, it’s called the four-way handshake.

Your computer, Computer 1,  begins this long farewell by sending a FIN (Finish) packet. This is your computer’s way of saying, “Okay, I don’t want to talk anymore.” A little socially awkward, but at least your computer’s intentions are clear.

Computer 2 responds by sending an ACK packet back to Computer 1, acknowledging Computer 1’s desire to end the conversation. 

Computer 2 sends another packet, a FIN packet, to Computer 1. This is Computer 2’s way of saying, “Yes, this conversation is over.”

Computer 1 sends one last ACK packet back over to Computer 2 to confirm that the conversation is, indeed, over.

So, the four steps for the four-way handshake are:

&nbsp;

1. Computer 1 sends a FIN packet to Computer 2
2. Computer 2 sends an ACK packet to Computer 1
3. Computer 2 sends a FIN packet to Computer 1
4. Computer 1 sends an ACK packet to Computer 2

&nbsp;

And with that, Computer 1 and Computer 2 part ways.

&nbsp;

#### WHO STARTS AND ENDS THE CONVERSATION?

Typically, the client (that’s you) will initialize the three-way handshake that establishes the connection. This happens because you click on a link, search for something, play a video, etc. However, either the client or the server could initialize the four-way handshake.

&nbsp;

#### SYN ERROR

Sometimes, you might see a “SYN error” in Wireshark. This means that your computer is socially awkward and there are no other computers or servers that want to talk to it.

Okay, that’s only sort of true. In reality, your computer tried to send a SYN packet, but it wasn’t received. There are a multitude of reasons why this could happen. Perhaps that will be covered in another post.

&nbsp;

#### CONCLUSION

In my next post in the Getting Started with Wireshark series, I’ll guide you through using filters to isolate SYN packets. Now that you’ve got some background knowledge, you’re ready to get a little more hands-on with Wireshark!

&nbsp;

# 🤝