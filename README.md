# STM32

11223

# STM32 Development Environment Setup

## 0.Prerequisite

```
sudo apt install build-essential git zlib1g-dev libsdl1.2-dev automake* autoconf* libtool libpixman-1-dev lib32gcc1 lib32ncurses5 libc6:i386 libncurses5:i386 libstdc++6:i386 libusb-1.0.0-dev
```

## 1.OpenOCD

```
git clone git://git.code.sf.net/p/openocd/code openocd
cd openocd
./bootstrap
./configure --prefix=/usr/local  --enable-jlink --enable-amtjtagaccel --enable-buspirate  --enable-stlink   --disable-libftdi
echo -e "all:\ninstall:" > doc/Makefile
make -j4
sudo make install
```

## 2. ST-LINK

```
git clone http://github.com/texane/stlink.git
cd stlink
mkdir build
cd build
cmake ..
make -j4
sudo make install
#sudo cp 49-stlinkv2.rules /etc/udev/rules.d/
```

## 3. ARM GCC toolchain 5.4

```
wget https://launchpad.net/gcc-arm-embedded/5.0/5-2016-q3-update/+download/gcc-arm-none-eabi-5_4-2016q3-20160926-linux.tar.bz2
tar -jxf gcc-arm-none-eabi-5_4-2016q3-20160926-linux.tar.bz2
rm gcc-arm-none-eabi-5_4-2016q3-20160926-linux.tar.bz2
```

edit "~/.bashrc" and append the following instruction:

```
PATH=$PATH:~/workspace/tools/gcc-arm-none-eabi-5_4-2016q3/bin
```

## 4. Fix USB-TTL module's permission denied error

```
sudo gpasswd --add username dialout
```
