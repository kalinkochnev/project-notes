## Setting up on school wifi
https://github.com/deepwithin/Raspberry-pi-to-university-wifi

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network = {
     ssid="UCONN-SECURE"
     scan_ssid=1
     mode=0
     key_mgmt=WPA-EAP
     pairwise=CCMP TKIP
     eap=PEAP
     identity="kak21001"         
     password="m5#70Z9U@kl36KP"
     phase1="peaplabel=0"
     phase2="auth=MSCHAPV2"
}
``````````````````````

- Make sure on UConn Guest because UConn Secure isn't supported
- Pretty much the only way to get the IP is if the pi has desktop mode.
The IP when in E2 is resonant@10.66.53.230
- When listing ifconfig, look for an inet that starts with 10.66
