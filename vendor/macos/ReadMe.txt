
libft4222 for Mac
-------------------

FTDI's libft4222 allows access to, and control of, the FT4222H. 
Depending on configuration, the FT4222H presents 1, 2 or 4 interfaces 
for I2C, SPI and GPIO functions. Please search ftdichip.com for the 
FT4222H data sheet, and Application Note AN_329 which describes the 
libft4222 API. 

The Mac version of libft4222 includes  FTDI's 
libftd2xx which itself includes an unmodified version of libusb 
(http://libusb.info) which is distributed under the terms of the GNU 
Lesser General Public License (see http://www.gnu.org/licenses). Sources 
for libusb, plus re-linkable object files are included in the libftd2xx 
distribution, available from ftdichip.com. 


Installing
----------
1. sudo ./install4222.sh

This copies the library (libft4222.1.4.4.221.dylib, libftd2xx.dylib) and headers to 
/usr/local/lib and /usr/local/include respectively. 


Building
--------

1. cd examples

2. build an excutable file

for dynamic library
cc get-version.c -o version.out -lft4222 -lftd2xx  -Wl,-L/usr/local/lib

for static library
cc get-version.c -o version.out ../build/libft4222.a -lstdc++ -lpthread -lobjc -framework IOKit -framework CoreFoundation -Wall -Wextra

3. ./version.out

You should see a message similar to this:

    Chip version: 42220400, LibFT4222 version: 010404DD
    
If you see a message such as "No devices connected" or "No FT4222H detected",
this may indicate that: 

    a.  There is no FT4222H connected.  Check by running 'lsusb', which 
        should output something similar to:

        Bus 001 Device 005: ID 0403:601c Future Technology Devices International, Ltd

    b.  Your program did not run with sufficient privileges to access USB.
        Use 'sudo', or 'su', or run as root.

If you enable the SPI feature, please check the SS pin first. The SS pin must be tied to high when SPI master mode is enabled.

Release Notes
-------------


1.4.4.221
    o Enable position-independent code

1.4.4.188
    o Add API FT4222_GetChipMode

1.4.4.169
    o Supported platforms : x86_64/arm64/arm64e
    o Remove libboost linking
    o	Add Feature. Add API FT4222_SPIMaster_SetMode
    o	Add static link support (already build in libftd2xx) 

1.4.4.48
    o	Fix issue. Frequency 100K~400K in I2C Master is not accurate.
    o	Add Feature. Add API FT4222_I2CMaster_ResetBus. This function can reset i2c bus when it is abnormal.
    o	Add Feature. Add API FT4222_SPIMaster_SetCS. It can determine the CS is high or low when SPI bus is active. The default value is active-low.
    o	Remove Feature. Remove API FT4222_SPISlave_RxQuickResponse. It may cause data lost sometimes.
    o	Add Feature. Add license announce in libft4222.h

1.4.2.184
     o	Fix issue. FT4222_I2CMaster_WriteEx does not return correct sizeTransferred.
     o	Fix issue. FT4222_SPIMaster_MultiReadWrite does not return correct sizeOfRead when multiReadBytes equal to zero
     
1.0.0.0
    Initial version.  Mac only.
