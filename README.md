Updated driver for rtl88x2bu wifi adaptors based on rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044.

Build confirmed on kernels up to 4.16.0.

See http://www.wolfteck.com/2018/02/22/wsky_1200mbps_wireless_usb_wifi_adapter/ for all the hows and whys around the updates.

# Fair warning...

I found the original source for this driver [on Dropbox](https://www.dropbox.com/s/b3muqkezsdirmje/Agedate-AC1200-New%20Driver%203.22-LINUX.zip) linked by the seller on [an Amazon listing](https://amzn.to/2Js9AL2).  Don't you love how reputable these driver bundles are?  Nothing say "no one tampered with this after it left the OEM" like downloading from Dropbox / Baidu / etc.

# DKMS installation

```bash
cd rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044
VER=$(cat ./version)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```
