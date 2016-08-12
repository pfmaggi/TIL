#  Scan your local wireless environment from the command line

When you click the Wi-Fi icon in OS X's menu bar (called AirPort before OS X Lion), you get a list of available wireless networks. The airport command-line utility does the same and a lot more. It shows you the numeric signal strength for every access point, the channel used, and the encryption level, if any.

Alas, the airport command-line utility is buried deep in the System directory (aka System folder when using OS X's GUI). But you can create a symbolic link to it using the one-time command below. Then just type airport -s in the Terminal's command line to get the detailed scan report. (Hint: If you don't get any output, turn Wi-Fi on in the Network system preference.)


To run a wireless scan:

    $ airport -s

Sample results:

       SSID BSSID             RSSI CHANNEL HT CC SECURITY (auth/unicast/group) 
       air4 90:84:0d:c2:c2:c2 -74    1     Y  US WPA2 (PSK/TKIP/TKIP) 
    MY408G1 00:26:b8:c2:c2:c2 -82    6     Y  US WEP 
       air4 00:24:36:c2:c2:c2 -27   11     Y  US WPA (PSK/TKIP/TKIP) 
    G00NOO7 00:18:01:c2:c2:c2 -70   11     N  US WEP 
    air4 5G 90:84:0d:c2:c2:c2 -87   36,+1  Y  US WPA2 (PSK/AES,TKIP/TKIP) 
    air4 5G 00:24:36:c2:c2:c2 -35  157,+1  Y  US WPA2 (PSK/AES,TKIP/TKIP)


[source](http://www.infoworld.com/article/2614879/mac-os-x/mac-os-x-top-20-os-x-command-line-secrets-for-power-users.html)
   
