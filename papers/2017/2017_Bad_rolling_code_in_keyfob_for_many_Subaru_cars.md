---
title: "Bad rolling code in keyfob for many Subaru cars"
year: "2017"
authors: "Tom Wimmenhove"
topics: "RKE Subaru Rolling Code Full Disclosure 433MHz"
url: "https://seclists.org/fulldisclosure/2017/Oct/27"
source: web
---

# Bad rolling code in keyfob for many Subaru cars

- **Year:** 2017  
- **Authors:** Tom Wimmenhove  
- **URL:** https://seclists.org/fulldisclosure/2017/Oct/27

---

Full Disclosure: Bad rolling code in keyfob for many Subaru cars

Bad rolling code in keyfob for many Subaru cars

From: Tom Wimmenhove &lt;tom.wimmenhove () gmail com&gt;
Date: Mon, 9 Oct 2017 16:27:57 -0400

[Author]

me &lt;tom.wimmenhove () gmail com&gt;

[Description of the vulnerability]

The rolling code used by the keyfob and car is predictable in the sense

that it is not random. It is simply incremental.

[Impact]

An attacker can &apos;clone&apos; the keyfob and, unlock cars and, when increasing

the rolling code with a sufficiently high value, effectively render the

user&apos;s keyfob unusable.

[Affected vehicles]

The exploit has only been tested on a 2009 Subaru Forester, but the same

fob is used, and the exploit should work on, the following vehicles:

- 2006 Subaru Baja

- 2005 - 2010 Subaru Forester

- 2004 - 2011 Subaru Impreza

- 2005 - 2010 Subaru Legacy

- 2005 - 2010 Subaru Outback

[Solution]

Don&apos;t use the most predictable sequential type of rolling code. Don&apos;t send

the command twice so that, in case of Samy Kamkar&apos;s rolljam attack, not

even the XOR checksum has to be recalculated when changing a lock to an

unlock command, since the 2 commands cancel each other out, leaving the

checksum in tact.

[Required hardware]

- Raspberry Pi B+ with WiFi dongle or Raspberry Pi Zero W with built-in

WiFi

- RTL-SDR RTL2832U DBV-T tuner ($10 on ebay)

- A piece of wire

- A 433MHz antenna

[Credit]

pmsac at toxyn dot org for figuring out the checksum algorithm

A detailed explanation of the inner workings of the exploit, how to set

things up and code for the exploit can be found on GitHub:

https://github.com/tomwimmenhove/subarufobrob

- Tom