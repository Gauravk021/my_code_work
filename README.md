Hi Team,

I’m experiencing repeated Citrix VDI lag, slow response, and intermittent disconnections while using My Windows 11 PWR.

Citrix Connection Diagnostics show:

* Connection quality: Fair/Poor
* Latency: 282 ms (previously around 235–300 ms)
* Wi-Fi signal: Good (-59 dBm)
* Protocol: TCP → SSL → CGP → ICA
* Gateway: GLOBAL.G.NSSVC.NET
* VDI hostname: CXUSTHQPWRZ1806
* VDA version: 2507.0.1101.2
* Workspace version: 26.3.20.31

I’ve already reset Citrix Workspace, restarted the laptop, and performed Wi-Fi, hotspot, and gateway connectivity tests. The issue persists.

Could the Citrix/VDI network team please investigate ICA RTT, jitter, packet loss, gateway routing, VDA host health, session reconnections, and whether EDT/UDP transport is available and permitted?

The Citrix Download Report and Copy Report functions are also not working. I can provide screenshots of the diagnostics.

Please help identify the root cause and restore a stable VDI connection.