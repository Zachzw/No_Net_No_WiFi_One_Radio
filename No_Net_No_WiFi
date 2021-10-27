from csclient import EventingCSClient
import time
cp = EventingCSClient('No_Net_No_WiFi')

while (True):
    time.sleep(600)
    status = cp.get('/status/wan/connection_state')
    radio_zero_status = cp.get('/config/wlan/radio/0/enabled')
    while status != 'connected':
        if radio_zero_status is True:
            cp.put('/config/wlan/radio/0/enabled', False)
            cp.log("WAN Disconnected - Disabling Wi-Fi Radio's")
            break
        elif radio_zero_status is not True:
            cp.log("WAN Disconnected - Leaving Radio's Disabled")
            break
    else:
        if radio_zero_status is True:
            cp.log("WAN Active - Radio's Staying Enabled")
            break
        else:
            cp.log("WAN Active - Leaving Radio's Disabled")
            break
    continue
