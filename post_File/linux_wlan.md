#linux_wlan

---

iwconfig wlan0 txpower on

iwlist wlan0 scan

iwconfig wlan0 essid “MyHome”

iwconfig wlan0 essid “MyHome” key 0123-4567-89

iwconfig wlan0

ifconfig wlan0 up

dhclient wlan0

dhcpcd wlan0

/etc/wpa_supplicant.conf

network={

        ssid="111"	

        psk="222"

}
