Hello, GitHub Community! 👋

Are you looking for a WiFi adapter for pentesting, but all the recommended models are super expensive or hard to find?
I was in the same situation, almost buying a $200 adapter, until I found a generic one at home. I decided to give it a try—and to my surprise, it worked perfectly in monitor mode and supported packet injection!

Here’s my story and a step-by-step guide so you can try it too.


---

The Adapter

Brand: Generic (Realtek RTL8188FTV)

Model: 802.11b/g/n 1T1R 2.4G WLAN Adapter

USB ID: 0bda:f179

Tested on: Kali Linux 32 bits (latest version, recent kernel)



---

How to Check If Yours Will Work

1. Plug in your adapter and open a terminal:

lsusb

Look for something like:

Realtek Semiconductor Corp. RTL8188FTV 802.11b/g/n 1T1R 2.4G WLAN Adapter


2. Enable monitor mode:

sudo airmon-ng start wlan0

If you see monitor mode enabled, you’re on the right track!


3. Test packet injection:

sudo aireplay-ng --test wlan0mon

(Replace wlan0mon with your actual interface name if needed.)
If you see packets being injected—it works.




---

Driver & Firmware Installation

In my case, Kali did not detect it out of the box, but it worked perfectly after installing the firmware package:

sudo apt install firmware-realtek

No need to download or compile extra drivers.


> ⚠️ Warning:
On some occasions, installing drivers or enabling monitor mode caused a kernel panic (your system may freeze or crash).

If this happens: just force reboot your laptop (hold the power button until it shuts down, then turn it back on).

After rebooting, everything usually works fine.





---

Is It Good for Real Pentesting?

Works great as a backup or for learning/testing.

Limited range and sensitivity, but excellent for nearby WiFi networks and basic pentesting.



---

If you have que
stions, open an issue or a pull request. 🤗

