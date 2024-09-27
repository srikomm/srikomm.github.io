---
layout: page
title: Extend Wi-Fi Range using DHCP protocol
categories: [ productivity ]
date: 2023-09-21
published: true
tags:
  - productivity
author: srikomm
---

Finally I'm able to set it up, wired range extender, same SSID, two routers in two opposite corners of my house, coverage has been great, and devices are seamlessly switching between the two as well. Big thanks to [@mahendrabishnoi2](https://github.com/mahendrabishnoi2) for the solve 

Here's what I did:

- Turned on DHCP on the main router (it is on by default, but just mentioned in case)
- Changed the default IP of main router from 192.168.1.1 to 192.168.0.1 so that both my main router and secondary are on the same subnet (this had to be done because, the default IP in TP-Link routers is 192.168.0.1 whereas it's 192.168.1.1 for the nokia/airtel router provided by ISP and for some weird unknown reason, when initially I switched TP-Link to 192.168.1.x I was unable to access the router's configuration page, tested this with multiple routers, Archer A6 and Archer A9, both same behaviour)
- Added a static DHCP entry for my secondary router in the same subnet as my main router
- One mistake I did here initially was adding the mac address in this format 94-8B-5F-AF-23-3F whereas I should've added it in this format 94:8B:5F:AF:23:3F (PS Hackers in the forum, don't get excited, I've changed the mac address )
- Turned on my secondary router, without connecting it to anything, just connected my mac to its wi-fi and in the configuration page, changed its operation mode to access point mode
- Disabled DHCP on the secondary router
- By default, after switching the router to operation mode, it's switched to auto, but turned it off as it's better to have one router handle all the DHCP allocations
- Connected an ethernet cable from LAN port of the main router to WAN port of the secondary router. 
- Change the SSID and Password of both the routers to be same so that devices connecting via wi-fi, would think it's a single network and switch between both of them based on signal strength (Again this step is not required if you want different networks from these routers).

Multiple caveats here:
- All the online guides asked me to connect the connect the cable to LAN ports on both the routers
- The LAN port on the main router that you're connecting your cable to, must be in route mode, not in bridge mode

