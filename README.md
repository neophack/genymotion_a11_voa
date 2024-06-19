# 挂载system.vmdk编辑

```
sudo guestmount -a system.vmdk -m /dev/sda4 --rw /mnt
sudo guestunmount /mnt

```

# Download [libhoudini](https://github.com/niizam/Genymotion_A11_libhoudini/releases/download/1.0/system.zip) from releases page.

# system 复制到/mnt

```
cp system/ /mnt -r
```

# 编辑build.prop
```
localhost:/mnt # echo 'ro.product.cpu.abilist=x86_64,x86,arm64-v8a,armeabi-v7a,armeabi
ro.product.cpu.abilist32=x86,armeabi-v7a,armeabi
ro.product.cpu.abilist64=x86_64,arm64-v8a
ro.vendor.product.cpu.abilist=x86_64,x86,arm64-v8a,armeabi-v7a,armeabi
ro.vendor.product.cpu.abilist32=x86,armeabi-v7a,armeabi
ro.vendor.product.cpu.abilist64=x86_64,arm64-v8a
ro.odm.product.cpu.abilist=x86_64,x86,arm64-v8a,armeabi-v7a,armeabi
ro.odm.product.cpu.abilist32=x86,armeabi-v7a,armeabi
ro.odm.product.cpu.abilist64=x86_64,arm64-v8a
ro.dalvik.vm.native.bridge=libhoudini.so
ro.enable.native.bridge.exec=1
ro.enable.native.bridge.exec64=1
ro.dalvik.vm.isa.arm=x86
ro.dalvik.vm.isa.arm64=x86_64
ro.zygote=zygote64_32' | tee -a system/build.prop >> system/vendor/build.prop
```

# 下载放置ova到~/.Genymobile/Genymotion/ova
# 删除原有~/.Genymobile/Genymotion/system-images/3.1.0/11.0.0
# 新建虚拟机选择安卓11

![image](https://github.com/neophack/genymotion_a11_voa/assets/12814250/0896f0b9-3302-477b-becc-981d64b5f154)

# 服务器运行genymotion
```
sudo apt install xvfb
Xvfb :99 -screen 0 1024x768x24 &
sudo apt-get install x11vnc
export DISPLAY=:99
x11vnc -display :99
```
