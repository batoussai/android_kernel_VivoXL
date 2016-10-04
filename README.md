# android_kernel_VivoXL

Blu Vivo XL kernel pretty much as provided by Blu,
I fixed the compilation errors and uploaded it. The same Kernel should be useful for development for the Gionee Elife S Plus and possibly phones that are basically rebrandings of the same (AFAIK unknown) chinese OEM.(Cherry Mobile and Star frequently share OEM with Blu and Gionee, might be worth checking)

Not sure about the dependencies you need since I built it in a machine I've been developing for a while, just follow any kernel compilation guide on XDA and you should get what you need.

Next up set your steps would be somewhat like:

export ARCH=arm64 
//to set the arquitecture you'll be compiling to

export CROSS_COMPILE=/path-to-your-toolchain/aarch64-linux-android-4.9/prebuilt/linux-x86_64/bin/aarch64-linux-android-
// set the path to your toolchain

Then:

make gionee6753_65u_l1_defconfig 
// to generate your config file, keep in mind that there are other defconf files which could mean there are other hardware variations out there, check your device's build.prop for a line like "build.flavor" or something like that and compare to the available defconfs under /arch/arm64/

and

./build.sh 
// to build

If all goes well this should get you a ZImage ready to be repacked with your phone's Ramdisk and flashed... that is if you manage to somehow unlock the bootloader and still get your phone to boot (certainly possible but I still don't know what steps ensure it'll work). 
