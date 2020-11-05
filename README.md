# esp8266_zb40_mqtt_gateway

Gateway for connecting GW60 superrollo shutters with ZB40 remote control unit with MQTT

For this to work you need to disable a remote and connect the ESP to the HCS361 KeeLoq chip (some soldering skills required)
This will definitely void your warranty, do it at your own risk!

This is a fork of https://github.com/thexperiments/esp8266_zb40_mqtt_gateway

I changed it, to stop the GW60 from moving while booting and to be able to use the remote manually, too.
(Some pins of the original version are set to "high" while booting, at least for NodeMCU Lolin V3)

Connections:

GPIO(arduino)|nodeMcu|HCS631
-------------|-------|------
14|D5|1(S0)
5|D1|2(S1)
4|D2|3(S2)
12|D6|4(S3)

For reset, set 13|D7 to ground.

The ESP will come up in AP mode for configuration with SSID ZB40_Gateway encryption is enabled. (Password: roottoor)

Default topic is /ZB40_GATEWAY.
You can controll it via MQTT with the following topics.

Topic|Payload (only one at a time)
-----|----------------------------
/ZB40_GATEWAY/ALL/|up, down, stop
/ZB40_GATEWAY/1/|up, down, stop
/ZB40_GATEWAY/2/|up, down, stop
/ZB40_GATEWAY/3/|up, down, stop

Based on example code:
https://github.com/tzapu/WiFiManager for config
https://github.com/knolleary/pubsubclient/ for mqtt

Thanks to the reasearch here:
https://forum.fhem.de/index.php?topic=17125.0

