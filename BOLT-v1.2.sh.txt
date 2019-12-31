#!/system/bin/sh
#
# BOLT v1.2
#
build='/system/build.prop' > /dev/null 2>&1;

#
# Bolt! | Boost
#
boost ( ) {
  busybox clear
  busybox echo " "
  busybox echo -e "Bolt! booster"
  busybox free | awk '/Mem/{print "Free Memory (Before Boost) : "$4/1024" MB";}'
  busybox echo "";
  busybox echo "";
  busybox echo "";
  busybox echo -n " Working";
  sync;
  busybox sleep 1
  busybox echo -n ".";
  busybox echo "3" > /proc/sys/vm/drop_caches;
  busybox sleep 1
  echo -n ".";
  dc=/proc/sys/vm/drop_caches
  dc_v=`cat $dc`
  if [ "$dc_v" -gt 1 ]; then
	  echo "1" > /proc/sys/vm/drop_caches;
  else
	  echo " Error When Boosting ! ";
	exit
  fi
  sleep 1
  echo -n ".";
  echo "";
  busybox echo ""
  busybox echo "Killing media processor & Media Server..."
  busybox sleep 1
  busybox killall -9 android.process.media
  busybox killall -9 mediaserver
  busybox echo ""
  busybox echo "Media Processor & Media Server has been killed..."
  sleep 1
  echo "";
  echo "  =- Boosted=-  ";
  echo "";
  echo "";
  echo "";
  busybox free | awk '/Mem/{print "Free Memory (After Boost) : "$4/1024" MB";}'
  echo "";
  echo "";
  busybox sleep 1
}
#
# Bolt! | Fstrim
#
fstrim_now ( ) {
	busybox echo "Applying Fstrim..."
	busybox sleep 1
	busybox echo ""
	if [ -d /cache ]
	then
	  busybox fstrim -v /cache
	  busybox sleep 0.5
	fi
	if [ -d /data ]
	then
	  busybox fstrim -v /data
	  busybox sleep 0.5
	fi
	if [ -d /system ]
	then
	  busybox fstrim -v /system
	  busybox sleep 0.5
	fi
	if [ -d /magisk ]
	then
	  busybox fstrim -v /magisk
	  busybox sleep 0.5
	fi
	if [ -d /preload ]
	then
	  busybox fstrim -v /preload
	  busybox sleep 0.5
	fi
	if [ -d /data/sdext2 ]
	then
	  busybox fstrim -v /data/sdext2
	  busybox sleep 0.5
	fi
	busybox echo ''
	busybox sleep 1
	busybox echo "Fstrim Done!"
}
#
# GPU Rendering
#
gpu_rendering ( ) {
	if busybox grep -q hw2d.force=1 $build && busybox grep -q hw3d.force=1 $build && busybox grep -q ro.product.gpu.driver=1 $build && busybox grep -q persist.sampling_profiler=0 $build && busybox grep -q hwui.render_dirty_regions=false $build && busybox grep -q persist.sys.ui.hw=1 $build && busybox grep -q ro.config.disable.hw_accel=false $build && busybox grep -q video.accelerate.hw=1 $build && busybox grep -q hwui.disable_vsync=true $build && busybox grep -q persist.sys.composition.type=gpu $build && busybox grep -q debug.sf.hw=1 $build && busybox grep -q debug.performance.tuning=1 $build && busybox grep -q video.accelerate.hw=1 $build && busybox grep -q debug.egl.profiler=1 $build && busybox grep -q debug.egl.hw=1 $build && busybox grep -q debug.composition.type=gpu $build && busybox grep -q debug.enabletr=true $build && busybox grep -q debug.overlayui.enable=1 $build && busybox grep -q debug.qctwa.preservebuf=1 $build && busybox grep -q dev.pm.dyn_samplingrate=1 $build && busybox grep -q ro.fb.mode=1 $build && busybox grep -q ro.sf.compbypass.enable=0 $build
	then
		busybox sed -i '/hw2d.force/d' $build
		busybox sed -i '/hw3d.force/d' $build
		busybox sed -i '/ro.product.gpu.driver/d' $build
		busybox sed -i '/persist.sampling_profiler/d' $build
		busybox sed -i '/hwui.render_dirty_regions/d' $build
		busybox sed -i '/persist.sys.ui.hw/d' $build
		busybox sed -i '/ro.config.disable.hw_accel/d' $build
		busybox sed -i '/video.accelerate.hw/d' $build
		busybox sed -i '/hwui.disable_vsync/d' $build
		busybox sed -i '/persist.sys.composition.type/d' $build
		busybox sed -i '/debug.sf.hw/d' $build
		busybox sed -i '/debug.performance.tuning/d' $build
		busybox sed -i '/video.accelerate.hw/d' $build
		busybox sed -i '/debug.egl.profiler/d' $build
		busybox sed -i '/debug.egl.hw/d' $build
		busybox sed -i '/debug.composition.type/d' $build
		busybox sed -i '/debug.enabletr/d' $build
		busybox sed -i '/debug.overlayui.enable/d' $build
		busybox sed -i '/debug.qctwa.preservebuf/d' $build
		busybox sed -i '/dev.pm.dyn_samplingrate/d' $build
		busybox sed -i '/ro.fb.mode/d' $build
		busybox sed -i '/ro.sf.compbypass.enable/d' $build
	else
		busybox sed -i '/hw2d.force/d' $build
		busybox sed -i '/hw3d.force/d' $build
		busybox sed -i '/ro.product.gpu.driver/d' $build
		busybox sed -i '/persist.sampling_profiler/d' $build
		busybox sed -i '/hwui.render_dirty_regions/d' $build
		busybox sed -i '/persist.sys.ui.hw/d' $build
		busybox sed -i '/ro.config.disable.hw_accel/d' $build
		busybox sed -i '/video.accelerate.hw/d' $build
		busybox sed -i '/hwui.disable_vsync/d' $build
		busybox sed -i '/persist.sys.composition.type/d' $build
		busybox sed -i '/debug.sf.hw/d' $build
		busybox sed -i '/debug.performance.tuning/d' $build
		busybox sed -i '/video.accelerate.hw/d' $build
		busybox sed -i '/debug.egl.profiler/d' $build
		busybox sed -i '/debug.egl.hw/d' $build
		busybox sed -i '/debug.composition.type/d' $build
		busybox sed -i '/debug.enabletr/d' $build
		busybox sed -i '/debug.overlayui.enable/d' $build
		busybox sed -i '/debug.qctwa.preservebuf/d' $build
		busybox sed -i '/dev.pm.dyn_samplingrate/d' $build
		busybox sed -i '/ro.fb.mode/d' $build
		busybox sed -i '/ro.sf.compbypass.enable/d' $build
		busybox echo 'hw2d.force=1' >> $build
		busybox echo 'hw3d.force=1' >> $build
		busybox echo 'ro.product.gpu.driver=1' >> $build
		busybox echo 'persist.sampling_profiler=0' >> $build
		busybox echo 'hwui.render_dirty_regions=false' >> $build
		busybox echo 'persist.sys.ui.hw=1' >> $build
		busybox echo 'ro.config.disable.hw_accel=false' >> $build
		busybox echo 'video.accelerate.hw=1' >> $build
		busybox echo 'hwui.disable_vsync=true' >> $build
		busybox echo 'persist.sys.composition.type=gpu' >> $build
		busybox echo 'debug.sf.hw=1' >> $build
		busybox echo 'debug.performance.tuning=1' >> $build
		busybox echo 'video.accelerate.hw=1' >> $build
		busybox echo 'debug.egl.profiler=1' >> $build
		busybox echo 'debug.egl.hw=1' >> $build
		busybox echo 'debug.composition.type=gpu' >> $build
		busybox echo 'debug.enabletr=true' >> $build
		busybox echo 'debug.overlayui.enable=1' >> $build
		busybox echo 'debug.qctwa.preservebuf=1' >> $build
		busybox echo 'dev.pm.dyn_samplingrate=1' >> $build
		busybox echo 'ro.fb.mode=1' >> $build
		busybox echo 'ro.sf.compbypass.enable=0' >> $build
	fi
}

#
# Smooth UI
#
smooth_ui ( ) {
	if busybox grep -q touch.pressure.scale=0.001 $build
	then
		busybox sed -i '/touch.pressure.scale/d' $build
	else
		busybox sed -i '/touch.pressure.scale/d' $build
		busybox echo 'touch.pressure.scale=0.001' >> $build
	fi
}
#
# HQ Graphics
#
hq_graphics ( ) {
	if busybox grep -q persist.sys.force_highendgfx=true $build
	then
		busybox sed -i '/persist.sys.force_highendgfx/d' $build
	else
		busybox sed -i '/persist.sys.force_highendgfx/d' $build
		busybox echo 'persist.sys.force_highendgfx=true' >> $build
	fi
}
#
# Cloudflare Dns
#
cloudflare_dns ( ) {
	if busybox grep -q net.dns1=1.1.1.1 $build && busybox grep -q net.dns2=1.0.0.1 $build && busybox grep -q net.eth0.dns1=1.1.1.1 $build && busybox grep -q net.eth0.dns2=1.0.0.1 $build && busybox grep -q net.rmnet0.dns1=1.1.1.1 $build && busybox grep -q net.rmnet0.dns2=1.0.0.1 $build && busybox grep -q net.rmnet1.dns1=1.1.1.1 $build && busybox grep -q net.rmnet1.dns2=1.0.0.1 $build && busybox grep -q net.rmnet2.dns1=1.1.1.1 $build && busybox grep -q net.rmnet2.dns2=1.0.0.1 $build && busybox grep -q net.wlan0.dns1=1.1.1.1 $build && busybox grep -q net.wlan0.dns2=1.0.0.1 $build && busybox grep -q dhcp.eth0.dns1=1.1.1.1 $build && busybox grep -q dhcp.eth0.dns2=1.0.0.1 $build && busybox grep -q dhcp.wlan0.dns1=1.1.1.1 $build && busybox grep -q dhcp.wlan0.dns2=1.0.0.1 $build
	then
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
	else
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
		busybox echo 'net.dns1=1.1.1.1' >> $build
		busybox echo 'net.dns2=1.0.0.1' >> $build
		busybox echo 'net.eth0.dns1=1.1.1.1' >> $build
		busybox echo 'net.eth0.dns2=1.0.0.1' >> $build
		busybox echo 'net.rmnet0.dns1=1.1.1.1' >> $build
		busybox echo 'net.rmnet0.dns2=1.0.0.1' >> $build
		busybox echo 'net.rmnet1.dns1=1.1.1.1' >> $build
		busybox echo 'net.rmnet1.dns2=1.0.0.1' >> $build
		busybox echo 'net.rmnet2.dns1=1.1.1.1' >> $build
		busybox echo 'net.rmnet2.dns2=1.0.0.1' >> $build
		busybox echo 'net.wlan0.dns1=1.1.1.1' >> $build
		busybox echo 'net.wlan0.dns2=1.0.0.1' >> $build
		busybox echo 'dhcp.eth0.dns1=1.1.1.1' >> $build
		busybox echo 'dhcp.eth0.dns2=1.0.0.1' >> $build
		busybox echo 'dhcp.wlan0.dns1=1.1.1.1' >> $build
		busybox echo 'dhcp.wlan0.dns2=1.0.0.1' >> $build
	fi
}
#
# Google Dns
#
google_dns ( ) {
	if busybox grep -q net.dns1=8.8.8.8 $build && busybox grep -q net.dns2=8.8.4.4 $build && busybox grep -q net.eth0.dns1=8.8.8.8 $build && busybox grep -q net.eth0.dns2=8.8.4.4 $build && busybox grep -q net.rmnet0.dns1=8.8.8.8 $build && busybox grep -q net.rmnet0.dns2=8.8.4.4 $build && busybox grep -q net.rmnet1.dns1=8.8.8.8 $build && busybox grep -q net.rmnet1.dns2=8.8.4.4 $build && busybox grep -q net.rmnet2.dns1=8.8.8.8 $build && busybox grep -q net.rmnet2.dns2=8.8.4.4 $build && busybox grep -q net.wlan0.dns1=8.8.8.8 $build && busybox grep -q net.wlan0.dns2=8.8.4.4 $build && busybox grep -q dhcp.eth0.dns1=8.8.8.8 $build && busybox grep -q dhcp.eth0.dns2=8.8.4.4 $build && busybox grep -q dhcp.wlan0.dns1=8.8.8.8 $build && busybox grep -q dhcp.wlan0.dns2=8.8.4.4 $build
	then
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
	else
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
		busybox echo 'net.dns1=8.8.8.8' >> $build
		busybox echo 'net.dns2=8.8.4.4' >> $build
		busybox echo 'net.eth0.dns1=8.8.8.8' >> $build
		busybox echo 'net.eth0.dns2=8.8.4.4' >> $build
		busybox echo 'net.rmnet0.dns1=8.8.8.8' >> $build
		busybox echo 'net.rmnet0.dns2=8.8.4.4' >> $build
		busybox echo 'net.rmnet1.dns1=8.8.8.8' >> $build
		busybox echo 'net.rmnet1.dns2=8.8.4.4' >> $build
		busybox echo 'net.rmnet2.dns1=8.8.8.8' >> $build
		busybox echo 'net.rmnet2.dns2=8.8.4.4' >> $build
		busybox echo 'net.wlan0.dns1=8.8.8.8' >> $build
		busybox echo 'net.wlan0.dns2=8.8.4.4' >> $build
		busybox echo 'dhcp.eth0.dns1=8.8.8.8' >> $build
		busybox echo 'dhcp.eth0.dns2=8.8.4.4' >> $build
		busybox echo 'dhcp.wlan0.dns1=8.8.8.8' >> $build
		busybox echo 'dhcp.wlan0.dns2=8.8.4.4' >> $build
	fi
}
#
# Bolt! Custom DNS
#
custom_dns ( ) {
	busybox clear
	busybox echo -e "Enter DNS 1"
	busybox echo -e "[CHOOSE] :"
	read -r DNS
	if [ "$DNS" == "" ]
	then
	  busybox clear
	  busybox echo "Nothing Entered"
	  busybox sleep 3
	  return 1
	fi
    no=$(busybox echo -e $DDNS | tr -d '0-9' '.')
    yes=$(busybox echo -e $DNS | tr -d 'a-z' 'A-Z')
    if [ "$no" ]; then
      busybox clear
      busybox echo 'Numbers and "." only'
      busybox sleep 3
      return 1
    elif [ "$yes" ]
    then
      busybox clear
      busybox echo "Enter DNS 2"
      busybox echo "[CHOOSE] :"
      read -r DNS2
      if [ "$DNS2" == "" ]
	  then
	    busybox clear
	    busybox echo "Nothing Entered"
	    busybox sleep 3
	    return 1
	  fi
    no=$(busybox echo -e $DDNS2 | tr -d '0-9' '.')
    yes=$(busybox echo -e $DNS2 | tr -d 'a-z' 'A-Z')
    if [ "$no" ]; then
      busybox clear
      busybox echo 'Numbers and "." only'
      busybox sleep 3
      return 1
    elif [ "$yes" ]
    then
	  if busybox grep -q net.dns1=$DNS $build && busybox grep -q net.dns2=$DNS2 $build && busybox grep -q net.eth0.dns1=$DNS $build && busybox grep -q net.eth0.dns2=$DNS2 $build && busybox grep -q net.rmnet0.dns1=$DNS $build && busybox grep -q net.rmnet0.dns2=$DNS2 $build && busybox grep -q net.rmnet1.dns1=$DNS $build && busybox grep -q net.rmnet1.dns2=$DNS2 $build && busybox grep -q net.rmnet2.dns1=$DNS $build && busybox grep -q net.rmnet2.dns2=$DNS2 $build && busybox grep -q net.wlan0.dns1=$DNS $build && busybox grep -q net.wlan0.dns2=$DNS2 $build && busybox grep -q dhcp.eth0.dns1=$DNS $build && busybox grep -q dhcp.eth0.dns2=$DNS2 $build && busybox grep -q dhcp.wlan0.dns1=$DNS $build && busybox grep -q dhcp.wlan0.dns2=$DNS2 $build
	  then
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
	  else
		busybox sed -i '/net.dns1/d' $build
		busybox sed -i '/net.dns2/d' $build
		busybox sed -i '/net.eth0.dns1/d' $build
		busybox sed -i '/net.eth0.dns2/d' $build
		busybox sed -i '/net.rmnet0.dns1/d' $build
		busybox sed -i '/net.rmnet0.dns2/d' $build
		busybox sed -i '/net.rmnet1.dns1/d' $build
		busybox sed -i '/net.rmnet1.dns2/d' $build
		busybox sed -i '/net.rmnet2.dns1/d' $build
		busybox sed -i '/net.rmnet2.dns2/d' $build
		busybox sed -i '/net.wlan0.dns1/d' $build
		busybox sed -i '/net.wlan0.dns2/d' $build
		busybox sed -i '/dhcp.eth0.dns1/d' $build
		busybox sed -i '/dhcp.eth0.dns2/d' $build
		busybox sed -i '/dhcp.wlan0.dns1/d' $build
		busybox sed -i '/dhcp.wlan0.dns2/d' $build
		busybox echo 'net.dns1='$DNS >> $build
		busybox echo 'net.dns2='$DNS2 >> $build
		busybox echo 'net.eth0.dns1='$DNS >> $build
		busybox echo 'net.eth0.dns2='$DNS2 >> $build
		busybox echo 'net.rmnet0.dns1='$DNS >> $build
		busybox echo 'net.rmnet0.dns2='$DNS2 >> $build
		busybox echo 'net.rmnet1.dns1='$DNS >> $build
		busybox echo 'net.rmnet1.dns2='$DNS2 >> $build
		busybox echo 'net.rmnet2.dns1='$DNS >> $build
		busybox echo 'net.rmnet2.dns2='$DNS2 >> $build
		busybox echo 'net.wlan0.dns1='$DNS >> $build
		busybox echo 'net.wlan0.dns2='$DNS2 >> $build
		busybox echo 'dhcp.eth0.dns1='$DNS >> $build
		busybox echo 'dhcp.eth0.dns2='$DNS2 >> $build
		busybox echo 'dhcp.wlan0.dns1='$DNS >> $build
		busybox echo 'dhcp.wlan0.dns2='$DNS2 >> $build
	  fi
	fi
  fi
}
#
# Reboot Options
#
soft_reboot ( ) {
  setprop ctl.restart zygote
}
reboots ( ) {
  reboot
  busybox sleep 3
  setprop sys.powerctl reboot
}
reboot_recovery ( ) {
  setprop ctl.start pre-recovery
  busybox sleep 3
  reboot recovery
}
restart_system_ui ( ) {
  service call activity 42 s16 com.android.systemui 
  am startservice -n com.android.systemui/.SystemUIService 
}
shutdown ( ) { 
  setprop sys.powerctl shutdown 
  busybox sleep 3
  reboot -p
}
  

busybox clear
busybox sleep 1
if [ "`id | grep =0`" ];
then
  busybox echo "You're in Super User Mode"
else
  busybox echo "You're not in Super User Mode?!"
  busybox echo "Are your phone is rooted?"
  busybox echo "Start first with 'su' command!"
  exit 1
fi
busybox echo "Loading Console..."
busybox sleep 3
busybox mount -o rw,remount /system

busybox clear
busybox echo "-----------------------------"
busybox echo "|       BOLT! CONSOLE       |"
busybox echo "-----------------------------"
busybox sleep 1
busybox echo "1. Dashboard"
busybox sleep 1
busybox echo "2. Boost Options"
busybox sleep 1
busybox echo "3. UI Optimization"
busybox sleep 1
busybox echo "4. Net Dns Changer"
busybox sleep 1
busybox echo "5. Adblock"
busybox sleep 1
busybox echo "6. Backup & Restore"
busybox sleep 1
busybox echo "7. Reboot Options"
busybox sleep 1
busybox echo "0. Exit"
busybox echo ""
busybox echo -n "[CHOOSE] :"
read -r menu
case $menu in
  1)
    while :
    do
      busybox echo "Dashboard"
      busybox echo ""
      busybox echo "1. Device Information"
      busybox echo "2. CPU Information"
      busybox echo "3. Kernel Information"
      busybox echo "0. Go Back"
      busybox echo ""
      busybox echo -n "[CHOOSE] :"
      read -r dashboard
      case $dashboard in
        1)
          model=$(getprop ro.product.model)
          android_version=$(getprop ro.build.version.release) > /dev/null 2>&1;
          sdk_version=$(getprop ro.build.version.sdk) > /dev/null 2>&1;
          manufacturer=$(getprop ro.product.manufacturer) > /dev/null 2>&1;
          brand=$(getprop ro.product.brand) > /dev/null 2>&1;
          hardware=$(getprop ro.hardware) > /dev/null 2>&1;
          id=$(getprop ro.build.id)
          busybox echo "Device Info"
          busybox echo ""
          busybox echo "Model : $model"
          busybox echo "Android Version : $android_version"
          busybox echo "SDK Version : $sdk_version"
          busybox echo "Manufacturer : $manufacturer"
          busybox echo "Brand : $brand"
          busybox echo "Hardware : $hardware"
          busybox echo "ID : $id"
          busybox echo ""
          busybox echo "Tap Enter to Go Back"
          read
          ;;
        2)
          busybox clear
          busybox echo "CPU Information"
          busybox echo ""
          busybox cat /proc/cpuinfo
          busybox echo ""
          busybox echo "Tap Enter to Go Back"
          read
          ;;
        3)
          busybox clear
          busybox echo "Kernel Information"
          busybox echo ""
          busybox cat /proc/version
          busybox echo ""
          busybox echo "Tap Enter to Go Back"
          read
          ;;
        0)
          busybox clear
          break
          ;;
      esac
      done
      ;;
  2)
    while :
    do
      busybox echo "Boost Options"
      busybox echo ""
      busybox echo "1. Boost Now"
      busybox echo "2. Fstrim Now"
      busybox echo "0. Go Back"
      busybox echo ""
      busybox echo -n "[CHOOSE] :"
      read -r boostopt
      case $boostopt in
        1)
          busybox clear
          busybox echo ""
          busybox sleep 3
          busybox echo ""
          boost
          ;;
        2)
          busybox clear
          busybox echo ""
          busybox sleep 3
          busybox echo ""
          fstrim_now
          ;;
       0)
          busybox clear
          break
          ;;
      esac
      done
      ;;
  3)
      while :
      do
      if busybox grep -q hw2d.force=1 $build && busybox grep -q hw3d.force=1 $build && busybox grep -q ro.product.gpu.driver=1 $build && busybox grep -q persist.sampling_profiler=0 $build && busybox grep -q hwui.render_dirty_regions=false $build && busybox grep -q persist.sys.ui.hw=1 $build && busybox grep -q ro.config.disable.hw_accel=false $build && busybox grep -q video.accelerate.hw=1 $build && busybox grep -q hwui.disable_vsync=true $build && busybox grep -q persist.sys.composition.type=gpu $build && busybox grep -q debug.sf.hw=1 $build && busybox grep -q debug.performance.tuning=1 $build && busybox grep -q video.accelerate.hw=1 $build && busybox grep -q debug.egl.profiler=1 $build && busybox grep -q debug.egl.hw=1 $build && busybox grep -q debug.composition.type=gpu $build && busybox grep -q debug.enabletr=true $build && busybox grep -q debug.overlayui.enable=1 $build && busybox grep -q debug.qctwa.preservebuf=1 $build && busybox grep -q dev.pm.dyn_samplingrate=1 $build && busybox grep -q ro.fb.mode=1 $build && busybox grep -q ro.sf.compbypass.enable=0 $build
      then
        GPU='ON'
      else
		GPU='OFF'
	  fi
      if busybox grep -q touch.pressure.scale=0.001 $build
	  then
		SUI='ON'
	  else
		SUI='OFF'
	  fi
      if busybox grep -q persist.sys.force_highendgfx=true $build
	  then
		HQG='ON'
	  else
		HQG='OFF'
	  fi
      busybox echo "UI Optimization"
      busybox echo ""
      busybox echo "1. High Quality Graphics | $HQG"
      busybox echo "2. GPU Rendering | $GPU"
      busybox echo "3. Smooth UI | $SUI"
      busybox echo "0. Go Back"
      busybox echo ""
      busybox echo -n "[CHOOSE] :"
      read -r ui
      case $ui in
        1)
          busybox clear
          hq_graphics
          ;;
        2)
          busybox clear
          gpu_rendering
          ;;
        3)
          busybox clear
          smooth_ui
          ;;
        0)
          busybox clear
          break
          ;;
      esac
      done
      ;;
  4)
    if busybox grep -q net.dns1=1.1.1.1 $build && busybox grep -q net.dns2=1.0.0.1 $build && busybox grep -q net.eth0.dns1=1.1.1.1 $build && busybox grep -q net.eth0.dns2=1.0.0.1 $build && busybox grep -q net.rmnet0.dns1=1.1.1.1 $build && busybox grep -q net.rmnet0.dns2=1.0.0.1 $build && busybox grep -q net.rmnet1.dns1=1.1.1.1 $build && busybox grep -q net.rmnet1.dns2=1.0.0.1 $build && busybox grep -q net.rmnet2.dns1=1.1.1.1 $build && busybox grep -q net.rmnet2.dns2=1.0.0.1 $build && busybox grep -q net.wlan0.dns1=1.1.1.1 $build && busybox grep -q net.wlan0.dns2=1.0.0.1 $build && busybox grep -q dhcp.eth0.dns1=1.1.1.1 $build && busybox grep -q dhcp.eth0.dns2=1.0.0.1 $build && busybox grep -q dhcp.wlan0.dns1=1.1.1.1 $build && busybox grep -q dhcp.wlan0.dns2=1.0.0.1 $build
	then
	  CLOUDFLARE='ON'
	  GOOGLE='OFF'
	elif busybox grep -q net.dns1=8.8.8.8 $build && busybox grep -q net.dns2=8.8.4.4 $build && busybox grep -q net.eth0.dns1=8.8.8.8 $build && busybox grep -q net.eth0.dns2=8.8.4.4 $build && busybox grep -q net.rmnet0.dns1=8.8.8.8 $build && busybox grep -q net.rmnet0.dns2=8.8.4.4 $build && busybox grep -q net.rmnet1.dns1=8.8.8.8 $build && busybox grep -q net.rmnet1.dns2=8.8.4.4 $build && busybox grep -q net.rmnet2.dns1=8.8.8.8 $build && busybox grep -q net.rmnet2.dns2=8.8.4.4 $build && busybox grep -q net.wlan0.dns1=8.8.8.8 $build && busybox grep -q net.wlan0.dns2=8.8.4.4 $build && busybox grep -q dhcp.eth0.dns1=8.8.8.8 $build && busybox grep -q dhcp.eth0.dns2=8.8.4.4 $build && busybox grep -q dhcp.wlan0.dns1=8.8.8.8 $build && busybox grep -q dhcp.wlan0.dns2=8.8.4.4 $build
	then
      CLOUDFLARE='OFF'
      GOOGLE='ON'
    else
      CLOUDFLARE='OFF'
      GOOGLE='OFF'
    fi
    while :
    do
    busybox clear
    busybox echo "Net Dns Changer"
    busybox echo ""
    busybox echo "1. Cloudflare DNS | $CLOUDFLARE"
    busybox echo "2. Google DNS | $GOOGLE"
    busybox echo "3. Custom DNS"
    busybox echo "0. Go Back"
    busybox echo ""
    busybox echo -e "[CHOOSE] :"
    read -r dns
    case $dns in
      1)
         busybox clear
         cloudflare_dns
         ;;
      2)
         busybox clear
         google_dns
         ;;
      3)
        busybox clear
        custom_dns
        ;;
      0)
         busybox clear
         break
         ;;
     esac
     done
     ;;
   5)
     busybox clear
     busybox rm -rf /system/etc/hosts
     busybox wget -O /system/etc/hosts http://goodbyeads.weebly.com/uploads/1/2/2/1/122145164/goodbyeads.txt
     busybox chmod 644 /system/etc/hosts
     busybox chown 0:0 /system/etc/hosts
     ;;
   6)
     while :
     do
     busybox clear
     busybox mkdir /system/BOLT
     busybox mkdir /system/BOLT/backup
     busybox chmod 755 /system/BOLT
     busybox chown 0:0 /system/BOLT
     busybox echo "Backup & Restore"
     busybox echo ""
     busybox echo "1. Backup build.prop"
     busybox echo "2. Backup hosts file"
     busybox echo "3. Restore build.prop"
     busybox echo "4. Restore hosts file"
     busybox echo "0. Go Back"
     busybox echo ""
     busybox echo -n "[CHOOSE] :"
     read -r backup
     case $backup in
       1)
         busybox clear
         busybox echo "Backing up build.prop..."
         busybox sleep 3
         busybox cp -f /system/build.prop /system/BOLT/backup/build.prop
         ;;
       2)
         busybox clear
         busybox echo "Backing up hosts file..."
         busybox sleep 3
         busybox cp -f /system/etc/hosts /system/BOLT/backup/hosts
         ;;
       3)
         busybox clear
         busybox echo "Restoring build.prop..."
         busybox sleep 3
         if [ -e /system/BOLT/backup/build.prop ]; then
           busybox cp -f /system/BOLT/backup/build.prop /system/build.prop
           busybox chmod 644 /system/build.prop
           busybox chown 0:0 /system/build.prop
         else
           busybox echo "No backup build.prop"
         fi
         ;;
       4)
         busybox echo "Restoring hosts file..."
         busybox sleep 3
         if [ -e /system/BOLT/backup/hosts ]; then
           busybox cp -f /system/BOLT/backup/hosts /system/etc/hosts
           busybox chmod 644 /system/etc/hosts
           busybox chown 0:0 /system/etc/hosts
         else
           busybox echo "No hosts file backup"
         fi
         ;;
       0)
         busybox clear
         break
         ;;
       esac
       done
       ;;
   7)
     while :
     do
     busybox clear
     busybox echo "Reboot Options"
     busybox echo ""
     busybox echo "1. Soft Reboot"
     busybox echo "2. Reboot"
     busybox echo "3. Reboot to Recovery"
     busybox echo "4. Reboot to Bootloader"
     busybox echo "5. Restart System UI"
     busybox echo "6. Shutdown"
     busybox echo "0. Go Back"
     busybox echo ""
     busybox echo -e "[CHOOSE] :"
     read -r ropt
     case $ropt in
       1)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         soft_reboot
         ;;
       2)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         reboots
         ;;
       3)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         reboot_recovery
         ;;
       4)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         reboot bootloader
         ;;
       5)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         restart_system_ui
         ;;
       6)
         busybox clear
         busybox echo "Please Wait..."
         busybox sleep 1
         busybox echo "5"
         busybox sleep 1
         busybox echo "4"
         busybox sleep 1
         busybox echo "3"
         busybox sleep 1
         busybox echo "2"
         busybox sleep 1
         busybox echo "1"
         busybox sleep 1
         shutdown
         ;;
       0)
         busybox clear
         break
         ;;
       esac
       done
       ;;
   0)
     busybox echo "Exiting..."
     busybox sleep 2
     busybox mount -o ro,remount /system
     exit
esac