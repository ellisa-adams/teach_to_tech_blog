---
author: Ellisa Adams
title: Getting Started with Wireshark - Part 3
date: 2024-07-02
description: We're capturing packets, not sharks...
tags: ["tech","Wireshark","Pcap"]
thumbnail:
  url: img/wireshark_3/wireshark_thumbnail.jpg
  author: Google images
---

### “Why, sometimes I’ve believed as many as six impossible things before breakfast.” 

#### Lewis Carroll (Through the Looking Glass)


&nbsp;

Let’s do a quick recap of the first two posts in the Getting Started with Wireshark series.

&nbsp;

1. Wireshark is an awesome program that can be downloaded at Wireshark.org.

2. Computers and servers are constantly talking to one another. They do this by sending packets.

3. Packets go to and fro according to their IP addresses.

4. When computers want to start a conversation, they send a set of specific packets and begin a three-way handshake.

5. When computers want to end a conversation, they send another set of specific packets and begin a four-way handshake.

&nbsp;

Here’s a new piece of information that I didn’t share in my last two posts. Those packets are being sent and received at a shockingly fast pace. In fact, since you started reading this, your computer has probably sent or received about 1,000 packets! Seems impossible, right? Wireshark can help you sort through them to find what you are looking for. In this post, I’ll introduce you to the basic layout of Wireshark and how to search for SYN packets.

&nbsp;

FOLLOW ALONG

&nbsp;

If you want to follow along, head on over to Wireshark.org’s example Skype file and download it. You can find it on this page: https://wiki.wireshark.org/Skype

Scroll down and click on the file called: SampleCaptures/SkypeIRC.cap

+++

&nbsp;

While you’re waiting for it to download, just a quick note:

If you were to open Wireshark without having downloaded a file, this is what you would see:

&nbsp;
{{< image src="img/wireshark_3/wireshark_3_activity.png" ratio="21x9" class="rounded" >}}
&nbsp;

You might not have activity levels (the squiggly lines) right away. Just give it a minute or two and you’ll see Wireshark picking up activity.

As you can see on mine, there is some activity going on at my house. Everything else is pretty quiet right now. If you were to click on Wi-Fi, Wireshark would open a new page and begin a packet capture on your Wi-Fi. The page would look just like the file I asked you to download from Wireshark.

&nbsp;

+++

#### LET’S DO THIS!

Now that you’ve downloaded the Skype file, go ahead and open it. Here’s what you will see:

&nbsp;

{{< image src="img/wireshark_3/wireshark_3_openingpage.png" ratio="21x9" class="rounded" >}}

&nbsp;

If you were watching this occur in realtime, you would see the files being listed at a surprising rate. However, this is just a trace file. Which basically means that at one point, someone did a packet capture on their computer. In this case, they were trying to highlight their interaction with Skype. The person running the packet capture saved it as a file and uploaded it to Wireshark.org for us to enjoy!

We could go into detail (SO much detail) about how to interpret all of the information within this file. However, this Wireshark series is meant for newcomers, so we’ll keep it simple for now.

&nbsp;

#### THE PACKET LIST (the pane with all the pretty colors)

{{< image src="img/wireshark_3/wireshark_3_packetlist2.png" ratio="21x9" class="rounded" >}}

The top pane is the packet list. The packet list is showing you your packets and a brief overview of where they’re coming from and where they’re going (the source and the destination). In this case, you can see the source IP and the destination IP. If you were running a packet capture on your own computer, you would be able to identify it right away! 

&nbsp;

**If you don’t know your IP address, open up command prompt and type this:
```
ipconfig
```

&nbsp;

The packet list has several fields. Let’s go over them:

No. - tells you the number of the individual packets.

Time - indicates the time each packet was sent (in seconds since the moment you started the capture).

Source - the source IP of the packet.

Destination - the destination IP of the packet.

Protocol - the packet’s protocol (TCP, UDP, etc.).

Length - the packet’s length in bytes.

Info - some “at a glance” info about the packet.

&nbsp;

#### COLORS

{{< image src="img/wireshark_3/wireshark_3_coloringrules.png" ratio="21x9" class="rounded" >}}

The colors of the packets and their meanings is a blog post all on its own. However, if you’re super curious, navigate to view and then click on coloring rules. You’ll be able to see what each color combination represents and the filter command that is being used. Notice that the SYN/FIN packets are all dark gray (this will be important later).

&nbsp;

#### PACKET DETAILS

{{< image src="img/wireshark_3/wireshark_3_PacketDetails.png" ratio="21x9" class="rounded" >}}

The bottom left pane is the packet details pane. This is showing you information about a single packet. Remember that each packet is numbered on the far left of the top window? You can click on a packet that you find interesting and view the information specific to that packet in the packet details pane.

&nbsp;

Go ahead and try it!

&nbsp;

As you click from one packet to the next, you will notice that each packet has several dropdown arrows in the packet details pane. If you click on those arrows, you can delve more deeply into the details of your packet.

&nbsp;

#### PACKET BYTES

{{< image src="img/wireshark_3/wireshark_3_packetbytes.png" ratio="21x9" class="rounded" >}}

The bottom right pane is the packet bytes pane. This pane shows you what the packet contains in byte form (more specifically, what you are seeing is the data offset in the gray column, sixteen hexadecimal bytes, and sixteen ASCII bytes.

&nbsp;

As you navigate between the packet details and packet bytes panes, you’ll notice that coordinating information from each pane is highlighted. In other words, when you click on something in the packet bytes pane, the information it is referring to will be highlighted in the packet details pane.

&nbsp;

#### PERSONAL PREFERENCE - Changing Packet Bytes to Packet Diagram

I am a very visual person. I love a good diagram. If you’re like me, you might prefer to change your packet bytes window to a packet diagram window. If you want to try it out, follow this path:

&nbsp;

Edit → Preferences → Appearance → Layout

&nbsp;

It will look like this: 

{{< image src="img/wireshark_3/wireshark_3_layout.png" ratio="21x9" class="rounded" >}}

&nbsp;

Under Pane 3, select “Packet Diagram” and click OK. Now your Wireshark trace file should look like this:  

{{< image src="img/wireshark_3/wireshark_3_pacdiagram.png" ratio="21x9" class="rounded" >}}

&nbsp;

If you really want to use this feature to it’s fullest extent, right click on the packet diagram window and select “Show Field Values”. It will now look like this:

{{< image src="img/wireshark_3/wireshark_3_pacdiagram2.png" ratio="21x9" class="rounded" >}}

The packet diagram layout with the field values displayed is great for those who are new to tech and are not yet familiar with reading bytes. 

&nbsp;

#### YOUR FIRST FILTER

This is a ton of information to take in at one time, and if you are just getting started, there’s plenty of opportunity to delve into the finer details of Wireshark. However, the real power of Wireshark is its ability to filter through these thousands of packets. So let’s try that!

&nbsp;

Above the packet list in Wireshark, you’ll see a little blue flag next to a white text box. I circled it below:

{{< image src="img/wireshark_3/wireshark_3_filter1.png" ratio="21x9" class="rounded" >}}

This is where you will type your first filter. 

&nbsp;

As promised in the previous blog post, we’re going to filter for SYN packets. We’re setting the SYN flag to True (1) and the ACK flag to False (0). To do that, we’ll use this filter:

&nbsp;

```
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

&nbsp;

Put the filter into the command line and press enter. This is what you should see:

&nbsp;

{{< image src="img/wireshark_3/wireshark_3_filter2.png" ratio="21x9" class="rounded" >}}

&nbsp;

Woohoo!

&nbsp;

The command line is green, which means that our filter is acceptable to Wireshark. If it had not been acceptable, the command line would be red. Also, remember the Coloring Rules? The SYN/FIN packets were identifiable by their dark gray coloring. This filter has successfully singled out the filtered packets!

&nbsp;

#### JUST A SECOND

“But wait!” you say, “These packets are not all gray, like the coloring rules stated!”

That’s true, I did point out that the SYN/FIN packets were gray, and as you can see, our resulting packets are mostly gray. The light green packet is part of an http session, hence the coloring. However, it is still a SYN packet, so it was included in the filtered group of packets. 

Similar logic applied with the black packets. These are bad tcp packets that Wireshark considered malformed. However, they were still intended to be SYN packets and are therefore included in the final results of the filter. 

See the image below to confirm that all of the packets are, indeed, SYN packets: 

{{< image src="img/wireshark_3/wireshark_3_syn.png" ratio="21x9" class="rounded" >}}

#### WHAT DOES IT ALL MEAN?

If you can identify the traffic occurring on your network, then you can monitor for any spurious activity. For example, you can check to see if there are foreign IP addresses active on your network. This would indicate that someone is using your Wi-Fi! Here’s another example: If you have a teenager, you can monitor the websites he or she is visiting (I won’t judge you for being protective). But before you address it with your teenager, Wireshark allows you the opportunity to corroborate the MAC addresses of the devices active on your network. After all, it might not be your teenager surfing the internet at 2 am. It could be the teenager two houses down!

However, it would be hard, impossible really, to spot suspicious packets when there are thousands of them every minute. But with the right filters, Wireshark can sort through the piles of packets for you. In doing so, Wireshark can help you do things that would otherwise be impossible!

In my next post, we’ll cover monitoring for suspicious activity with Wireshark. Stay tuned for this bonus post!

&nbsp;

# 🎉