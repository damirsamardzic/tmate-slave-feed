# tmate-slave-feed
OpenWrt feed for tmate-slave server (https://github.com/tmate-io/tmate-slave)

Tested on Raspberry Pi Model 3 B with OpenWrt master branch.
Debug is disabled for tmate-slave (with dummy hack on tmate-debug.c to avoid execinfo.h). TODO: see https://github.com/tmate-io/tmate/issues/83

Instructions:
```
git clone https://github.com/openwrt/openwrt.git
cd openwrt/
cp feeds.conf.default feeds.conf
echo "src-git tmate_slave_feed https://github.com/damirsamardzic/tmate-slave-feed.git" >> feeds.conf
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig       
```
- select target, subtarget for Pi 3
- select Network / tmate-slave
- select Global build settings / Enable kernel cgroups && Enable kernel namespace
```
make defconfig
make V=s
```
- answer with y once asked for CFQ Group Scheduling support 


Once OpenWrt boots up, tmate-slave is automatically started with keys generated in ```/etc/tmate-slave/keys``` directory.

Configuration is stored in ```/etc/config/tmate-slave```.

Start / stop commands:
```
/etc/init.d/tmate-slave stop
/etc/init.d/tmate-slave start
```
