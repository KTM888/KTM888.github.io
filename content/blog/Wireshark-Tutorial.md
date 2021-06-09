---
title: "Wireshark Turorial - Customising Columns and Layout for productivity"
date: Mon, 08 Sep 2019 14:09:10 +0000
image: /img/wireshark-front.png
draft: false
featured: true
description: "This a tutorial of wireshark (an open-source packet analyzer) that will teach you how to customize the layout and columns of the GUI interface to optimize your productivity while learning how to navegate through it properly and effectively."
tags: [Wireshark, Open-Source, Tutorials, customising]
---

# Intro

This a tutorial of wireshark (an open-source packet analyzer) that will teach you how to customize the layout and columns of the GUI interface to optimize your productivity while learning how to navegate through it properly and effectively.

# Web Traffic and the Default Wireshark Column Display

Malware distribution frequently occurs through web traffic, and we also see this channel used for data
exfiltration and command and control activity. Wireshark’s default column is not ideal when investigating such
malware-based infection traffic. However, Wireshark can be customized to provide a better view of the activity

img/Pasted image 20201116120912.png

## Wireshark’s default columns are:

- No. -Frame number from the beginning of the pcap. The first frame is always 1.
- Time – Seconds broken down to the nanosecond from the first frame of the pcap The first frame is always 0.000000.
- Source – Source address, commonly an IPv4, IPv6, or Ethernet address.
- Destination – Destination address, commonly an IPv4, IPv6, or Ethernet address.
- Protocol – Protocol used in the Ethernet frame, IP packet, or TCP segment (ARP, DNS, TCP, HTTP, etc.).
- Length – Length of the frame in bytes.

In my day-to-day work, I require the following columns in my Wireshark display:

- Date & time in UTC
- Source IP and source port
- Destination IP and destination port
- HTTP host
- HTTPS server
- Info
- How can we reach this state? First, we hide or remove the columns we do not want.

## Hiding Columns

We can easily hide columns in case we need them later. Right-click on any of the column headers to bring up
the column header menu. Then left-click any of the listed columns to uncheck them. Figure 2 shows the No.,
Protocol, and Length columns unchecked and hidden.

img/Pasted image 20201116121044.png

## Removing Columns

Because I never use the No., Protocol, or Length columns, I completely remove them. To remove columns,
right-click on the column headers you want to remove. Then select “Remove this Column…” from the column
header menu.

img/Pasted image 20201116121106.png

At this point, whether hidden or removed, the only visible columns are Time, Source, Destination, and Info.

## Adding Columns

To add columns in Wireshark, use the Column Preferences menu. Right-click on any of the column headers,
then select “Column Preferences…”

img/Pasted image 20201116121141.png

The Column Preferences menu lists all columns, viewed or hidden. Near the bottom left side of the Column
Preferences menu are two buttons. One has a plus sign to add columns. The other has a minus sign to
remove columns. Left-click on the plus sign. An entry titled “New Column” should appear at the bottom of the
column list.

img/Pasted image 20201116121158.png

Double-click on the “New Column” and rename it as “Source Port.” The column type for any new columns
always shows “Number.” Double-click on “Number” to bring up a menu, then scroll to “Src port (unresolved)”
and select that for the column type.

Pasted image 20201116121212.png

img/Pasted image 20201116121220.png

Our new column is now named “Source Port” with a column type of “Src port (unresolved).” Left-click on that
entry and drag it to a position immediately after the source address.

img/Pasted image 20201116121244.png

After the source port has been, add another column titled “Destination Port” with the column type “Dest port
(unresolved).”

img/Pasted image 20201116121304.png

Like we did with the source port column, drag the destination port to place it immediately after the Destination
address. When you finish, your columns should appear as shown in Figure 10.

img/Pasted image 20201116121331.png

After adding the source and destination port columns, click the “OK” button to apply the changes. These new
columns are automatically aligned to the right, so right-click on each column header to align them to the left,
so they match the other columns.

img/Pasted image 20201116121401.png

img/Pasted image 20201116121408.png

In my day-to-day work, I often hide the source address and source port columns until I need them.

## Changing Time to UTC

To change the time display format, go the “View” menu, maneuver to “Time Display Format,” and change the value from “Seconds Since Beginning of Capture” to “UTC Date and Time of Day.” Use the same menu path
to change the resolution from “Automatic” to “Seconds.” Figure 13 shows the menu paths for these options.

![[Pasted image 20201116121503.png]]

![[Pasted image 20201116121512.png]]

Wireshark column display.
To quickly find domains used in HTTP traffic, use the Wireshark filter http.request and examine the frame
details window.
In the frame details window, expand the line titled “Hypertext Transfer Protocol” by left clicking on the arrow
that looks like a greater than sign to make it point down. This reveals several additional lines. Scroll down to
the line starting with “Host:” to see the HTTP host name. Left click on this line to select it. Right click on the
line to bring up a menu. Near the top of this menu, select “Apply as Column.” This should create a new
column with the HTTP host name.

![[Pasted image 20201116121556.png]]

![[Pasted image 20201116121605.png]]

Below the “Handshake Protocol: Client Hello” line, expand the line that starts with “Extension: server_name.”
Under that is “Server Name Indication extension” which contains several Server Name value types when
expanded. Select the line that starts with “Server Name:” and apply it as a column. Figure 18 shows an
example.

![[Pasted image 20201116121619.png]]

![[Pasted image 20201116121628.png]]

With this customization, we can filter on http.request or ssl.handshake.type == 1 as shown in Figure 20.
This gives us a much better idea of web traffic in a pcap than using the default column display in Wireshark.

![[Pasted image 20201116121642.png]]

## Summary

This tutorial covered the following areas: - Web traffic and the default Wireshark column display - Hiding columns - Removing columns - Adding columns - Changing time to UTC - Custom columns

Wireshark customization is helpful for security professionals investigating suspicious network traffic. It can be
extremely useful when reviewing web traffic to determine an infection chain. Using the methods in this tutorial,
we can configure Wireshark’s column display to better fit our investigative workflow.
