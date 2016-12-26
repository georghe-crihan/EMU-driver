###################################################
#
# Makefile for EMUUSBAudio.kmod 
# Creator [Xcode -> Makefile Ver: Dec 23 2016 22:57:35]
# Created: [Sat Dec 24 00:08:11 2016]
#
# xcodebuild -verbose -sdk macosx10.9  MACOSX_DEPLOYMENT_TARGET=10.9 clean
#
# /Developer.4.6.3/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk/System/Library/Frameworks/Kernel.framework/Headers/IOKit/usb/USB.h
# #ifdef __clang__
#    #pragma options align=reset
# #else
#    #pragma pack()
# #endif
#
###################################################

#
# Macros
#

#CC = /usr/bin/gcc
CC = gcc-mp-5
LD = gcc-mp-5
# xcode 4.6.x
#LD = /Developer.4.6.3/Xcode.app/Contents/Developer/usr/bin/gcc
#CC = /Developer.4.6.3/Xcode.app/Contents/Developer/usr/bin/gcc
# xcode 5.1.1
#LD = /Developer.5.1.1/Xcode.app/Contents/Developer/usr/bin/gcc
#CC = /Developer.5.1.1/Xcode.app/Contents/Developer/usr/bin/gcc

CPU  := $(shell uname -m)
ifeq ($(CPU),i386)
FL_ARCH += -m32
else
ifeq ($(CPU),x86_64)
FL_ARCH += -m64
endif
endif

MACOS_VER=-mmacosx-version-min=10.8

# xcode 4.6.x
SDKROOT=/Developer.4.6.2/Xcode.app/Contents/Developer
SYSROOT=$(SDKROOT)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk
# xcode 5.1.1
#SDKROOT=/Developer.5.1.1/Xcode.app/Contents/Developer
#SYSROOT=$(SDKROOT)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.9.sdk

FL_WARNINGS+=-Wno-missing-field-initializers -Wno-missing-prototypes -Wno-non-virtual-dtor -Wno-overloaded-virtual -Wformat -Wno-missing-braces -Wparentheses -Wswitch -Wunused-function -Wno-unused-label -Wno-unused-parameter -Wunused-variable -Wunused-value -Wempty-body -Wno-unknown-pragmas -Wno-shadow -Wno-conversion -Wint-conversion 
#FL_WARNINGS+=-Wno-newline-eof -Wno-c++11-extensions -Wno-exit-time-destructors -Wno-four-char-constants
#FL_WARNINGS+=-Wenum-conversion -Wconstant-conversion -Wshorten-64-to-32

FL_DEFINES=-D_HULA_MACOSX_ -DKERNEL -DKERNEL_PRIVATE -DDRIVER_PRIVATE -DAPPLE -DNeXT

FL_INCLUDES=-iquote build/EMUUSBAudio.build/Release/EMUUSBAudio.build/EMUUSBAudio-generated-files.hmap \
-Ibuild/EMUUSBAudio.build/Release/EMUUSBAudio.build/EMUUSBAudio-own-target-headers.hmap \
-Ibuild/EMUUSBAudio.build/Release/EMUUSBAudio.build/EMUUSBAudio-all-target-headers.hmap \
-iquote build/EMUUSBAudio.build/Release/EMUUSBAudio.build/EMUUSBAudio-project-headers.hmap \
-Ibuild/Release/include \
-I$(SDKROOT)/Toolchains/XcodeDefault.xctoolchain/usr/include \
-I/System/Library/Frameworks/Kernel.framework/PrivateHeaders \
-I$(SYSROOT)/System/Library/Frameworks/Kernel.framework/Headers \
-Ibuild/EMUUSBAudio.build/Release/EMUUSBAudio.build/DerivedSources/i386 \
-Ibuild/EMUUSBAudio.build/Release/EMUUSBAudio.build/DerivedSources \
-Fbuild/Release \
-I$(SYSROOT)/System/Library/Frameworks/Kernel.framework/Versions/A/Headers/

#CC_OPTIONS = --sysroot $(SYSROOT) -std=c++11 -fapple-kext $(INCLUDES) $(FL_ARCH) -fno-builtin -nostdlib -r -Wall 
#CC_OPTIONS += -stdlib=libc++ -fasm-blocks
CC_OPTIONS += $(FL_ARCH) -fmessage-length=0 -nostdinc -std=gnu++11 \
-fno-builtin -Wno-trigraphs -fno-exceptions -fno-rtti -msoft-float -Os -fno-common -mkernel \
$(FL_WARNINGS) $(FL_DEFINES) -isysroot $(SYSROOT) -fapple-kext -fstrict-aliasing \
-Wdeprecated-declarations -Winvalid-offsetof -mmacosx-version-min=10.7 -g -Wno-sign-conversion \
$(FL_INCLUDES)

#FRAMEWORKS = \
#		-framework CoreAudioKit\
#		-framework CoreFoundation\
#		-framework CoreAudio\
#		-framework IOKit\
#		-L$(SYSROOT)/System/Library/Frameworks

LNK_OPTIONS = $(FRAMEWORKS) -Wall -r -lkmod -lcc_kext \
		-stdlib=libc++ -Xlinker -kext -nostdlib -lkmodc++ 

LNK_OPTIONS = $(FRAMEWORKS) -Wall -r -lkmod \
		-Xlinker -kext -nostdlib -lkmodc++ 

#
# INCLUDE directories for EMUUSBAudio.kmod
#

INCLUDE = -I.\
		-IEMUUSBAudio

#DEPINFO = -Xlinker -dependency_info -Xlinker EMUUSBAudio_dependency_info.dat

#
# Build EMUUSBAudio.kmod 
#

EMUUSBAudio.kmod : \
		./USB.o\
		./EMUUSBAudioDevice.o\
		./EMUUSBAudioEngine.o\
		./EMUXUCustomControl.o\
		./EMUUSBAudioLevelControl.o\
		./USBAudioObject.o\
		./EMUUSBAudioPlugin.o\
		./EMUUSBUserClient.o\
		./EMUUSBInputStream.o\
		./EMUUSBAudioClip.o\
		./IOUSBPipe.o\
		./IOUSBDevice.o\
		./IOUSBInterface.o\
		./LowPassFilter.o\
		./EMUUSBOutputStream.o\
		./StreamInfo.o
	$(LD) $(MACOS_VER) $(DEPINFO) $(LNK_OPTIONS) \
		./EMUUSBAudio_info.c\
		./USB.o\
		./EMUUSBAudioDevice.o\
		./EMUUSBAudioEngine.o\
		./EMUXUCustomControl.o\
		./EMUUSBAudioLevelControl.o\
		./USBAudioObject.o\
		./EMUUSBAudioPlugin.o\
		./EMUUSBUserClient.o\
		./EMUUSBInputStream.o\
		./EMUUSBAudioClip.o\
		./IOUSBPipe.o\
		./IOUSBDevice.o\
		./IOUSBInterface.o\
		./LowPassFilter.o\
		./EMUUSBOutputStream.o\
		./StreamInfo.o\
		-o EMUUSBAudio.kmod 

clean : 
		rm \
		./USB.o\
		./EMUUSBAudioDevice.o\
		./EMUUSBAudioEngine.o\
		./EMUXUCustomControl.o\
		./EMUUSBAudioLevelControl.o\
		./USBAudioObject.o\
		./EMUUSBAudioPlugin.o\
		./EMUUSBUserClient.o\
		./EMUUSBInputStream.o\
		./EMUUSBAudioClip.o\
		./IOUSBPipe.o\
		./IOUSBDevice.o\
		./IOUSBInterface.o\
		./LowPassFilter.o\
		./EMUUSBOutputStream.o\
		./StreamInfo.o\
		EMUUSBAudio.kmod

install : EMUUSBAudio.kmod 
		cp EMUUSBAudio.kmod ../v8/EMUUSBAudio.kext/Contents/MacOS/EMUUSBAudio
		sudo cp EMUUSBAudio.kmod /System/Library/Extensions/EMUUSBAudio.kext/Contents/MacOS/EMUUSBAudio

check :
	sudo kextutil -t /System/Library/Extensions/EMUUSBAudio.kext
	
#
# Build the parts of EMUUSBAudio.kmod 
#


# Item # 1 -- USB --
./USB.o : USB.cpp
	$(CC) $(CC_OPTIONS) USB.cpp -c $(INCLUDE) -o ./USB.o


# Item # 2 -- EMUUSBAudioDevice --
./EMUUSBAudioDevice.o : EMUUSBAudio/EMUUSBAudioDevice.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBAudioDevice.cpp -c $(INCLUDE) -o ./EMUUSBAudioDevice.o


# Item # 3 -- EMUUSBAudioEngine --
./EMUUSBAudioEngine.o : EMUUSBAudio/EMUUSBAudioEngine.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBAudioEngine.cpp -c $(INCLUDE) -o ./EMUUSBAudioEngine.o


# Item # 4 -- EMUXUCustomControl --
./EMUXUCustomControl.o : EMUUSBAudio/EMUXUCustomControl.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUXUCustomControl.cpp -c $(INCLUDE) -o ./EMUXUCustomControl.o


# Item # 5 -- EMUUSBAudioLevelControl --
./EMUUSBAudioLevelControl.o : EMUUSBAudio/EMUUSBAudioLevelControl.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBAudioLevelControl.cpp -c $(INCLUDE) -o ./EMUUSBAudioLevelControl.o


# Item # 6 -- USBAudioObject --
./USBAudioObject.o : EMUUSBAudio/USBAudioObject.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/USBAudioObject.cpp -c $(INCLUDE) -o ./USBAudioObject.o


# Item # 7 -- EMUUSBAudioPlugin --
./EMUUSBAudioPlugin.o : EMUUSBAudio/EMUUSBAudioPlugin.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBAudioPlugin.cpp -c $(INCLUDE) -o ./EMUUSBAudioPlugin.o


# Item # 8 -- EMUUSBUserClient --
./EMUUSBUserClient.o : EMUUSBAudio/EMUUSBUserClient.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBUserClient.cpp -c $(INCLUDE) -o ./EMUUSBUserClient.o


# Item # 9 -- EMUUSBInputStream --
./EMUUSBInputStream.o : EMUUSBAudio/EMUUSBInputStream.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBInputStream.cpp -c $(INCLUDE) -o ./EMUUSBInputStream.o


# Item # 10 -- EMUUSBAudioClip --
./EMUUSBAudioClip.o : EMUUSBAudioClip.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudioClip.cpp -c $(INCLUDE) -o ./EMUUSBAudioClip.o


# Item # 11 -- IOUSBPipe --
./IOUSBPipe.o : IOUSBPipe.cpp
	$(CC) $(CC_OPTIONS) IOUSBPipe.cpp -c $(INCLUDE) -o ./IOUSBPipe.o


# Item # 12 -- IOUSBDevice --
./IOUSBDevice.o : IOUSBDevice.cpp
	$(CC) $(CC_OPTIONS) IOUSBDevice.cpp -c $(INCLUDE) -o ./IOUSBDevice.o


# Item # 13 -- IOUSBInterface --
./IOUSBInterface.o : IOUSBInterface.cpp
	$(CC) $(CC_OPTIONS) IOUSBInterface.cpp -c $(INCLUDE) -o ./IOUSBInterface.o


# Item # 14 -- LowPassFilter --
./LowPassFilter.o : EMUUSBAudio/LowPassFilter.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/LowPassFilter.cpp -c $(INCLUDE) -o ./LowPassFilter.o


# Item # 15 -- EMUUSBOutputStream --
./EMUUSBOutputStream.o : EMUUSBAudio/EMUUSBOutputStream.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/EMUUSBOutputStream.cpp -c $(INCLUDE) -o ./EMUUSBOutputStream.o


# Item # 16 -- StreamInfo --
./StreamInfo.o : EMUUSBAudio/StreamInfo.cpp
	$(CC) $(CC_OPTIONS) EMUUSBAudio/StreamInfo.cpp -c $(INCLUDE) -o ./StreamInfo.o


##### END RUN ####
