FT4222H support lib 1.4.7 - Revision Comments 

The files included in a standard support lib release are:
•	D2XX Interface
	o	ftd2xx.h 
	o	Dynamic library (dll directory)
			i386\ftd2xx.lib (32-bit)
			amd64\ftd2xx.lib (64-bit)
	o	Static library (lib directory)
			i386\ftd2xx.lib (32-bit)
			amd64\ftd2xx.lib (64-bit)
•	FT4222H Interface
	o	LibFT4222.h
	o	Dynamic library (dll directory)
			i386\LibFT4222.dll (32-bit)
			i386\LibFT4222.lib (32-bit)
			amd64\LibFT4222-64.dll (64-bit)
			amd64\LibFT4222-64.lib (64-bit)

	o	Static library (lib directory)
			vs2013\i386\LibFT4222.lib (32-bit)
			vs2013\amd64\LibFT4222-64.lib (64-bit)
			ucrt\i386\LibFT4222.lib (32-bit)
			ucrt \amd64\LibFT4222-64.lib (64-bit)


•	Sample codes
o	In Sample folder, LibFT4222_examples.sln can be used to browser all samples.
o	This Sample code is linked to Dynamic library


On making a new release the files will be posted on FTDI’s web site http://www.ftdichip.com/Products/ICs/FT4222H.html in ZIP file format.


The dynamic library of Libft4222 is based on Microsoft Visual C++ 2015 x86 and x64 Redistributable package. If you want to build up a dynamic link executable file, please install the below package on the target machine.
https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170

For building up a static link executable file, libft4222 supports Visual Studio 2013 and Visual Studio which version is 2015 or advance. If the version of Visual Studio is equal to or greater than 2015, you need to link with the library in UCRT folder.

All the examples are built with dynamic link except “getting_started” project. “getting started” include both dynamic and static link example.
Starting from v1.4.6, the calling convention of our library has been changed to “stdcall”. Here are the notes on usage.
•	If there is a calling convention mismatch between the application and the DLL, recompiling the application is necessary to ensure that it understands and passes function parameters correctly.
•	If your x86 application is written in other languages (e.g. C#, Delphi, etc.) and calls C++ DLLs via P/Invoke or other mechanisms, then you need to ensure that the correct calling convention is used in those languages as well.
 
Release version
1.4.7 (October 30, 2024)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Fix csharp_spi_master complier issue.
o	Fix FT4222_GetVersion issue.
o	Add x64 examples.

Release version
1.4.6.1 (April 3, 2024)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Fix dll file does not be signed issue.

Release version
1.4.6 (March 7, 2024)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Add static lib support for VS2013 and the version is higher than VS2015(UCRT).
o	Add API FT4222_GetChipMode.
o	Calling convention is changed to “stdcall”.

Release version
1.4.5 (June 14, 2022)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Remove libboost linking.
o	Add Feature. Add API FT4222_SPIMaster_SetMode. It can change the polarity and phase
o	Change the member names in enum SPI_ChipSelect
o	Add event trigger in interrupt example
o	Microsoft Visual C++ 2010 runtime library is already built in

Release version
1.4.4 (Nov 12, 2020)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Fix issue. Frequency 100K~400K in I2C Master is not accurate.
o	Add Feature. Add API FT4222_I2CMaster_ResetBus. This function can reset i2c bus when it is abnormal.
o	Add Feature. Add API FT4222_SPIMaster_SetCS. It can determine the CS is high or low when SPI bus is active. The default value is active-low.
o	Remove Feature. Remove API FT4222_SPISlave_RxQuickResponse. It may cause data lost sometimes.
o	Add Feature. Add license announce in libft4222.h.
o	Add Feature. Add static library, need to define FT4222_STATIC during building.

Release version
1.4.3 (Mar 19, 2020)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Fix issue. FT4222_I2CMaster_WriteEx does not return correct sizeTransferred.
o	Fix issue. FT4222_SPIMaster_MultiReadWrite does not return correct sizeOfRead when multiReadBytes equal to zero.

Release version
1.4.2 (Dec 5, 2018)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Function changed. Now I2c master can send larger than 512 bytes.
o	Function changed. Adopt FT_SetTimeouts to be the default timeout of FT4222_I2CMaster_Read.

Release version
1.4.1 (Mar 15, 2018)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B”, “C” and “D”.
o	Fix FT4222_GetClock get error issue.
o	Fix issue. Repeated_START does not work in API. FT4222_I2CMaster_WriteEx.
o	Fix issue. FT4222_UnInitialize hang on linux platform in SPI Slave Mode.
o	Fix issue. SPI slave cannot receive more than 8192 bytes in SPI with protocol mode.
o	FT4222_I2CMaster_Init can support speed < 60K bps. 
o	Add API FT4222_ChipReset.
o	Add API FT4222_SPISlave_SetMode.
o	Add API FT4222_GPIO_SetWaveFormMode(only available in Chip Rev D).
o	Add API FT4222_SPISlave_RxQuickResponse (only available in Chip Rev D).
o	Add SPI flash access examples.
o	Add SPI Slave sample(NO protocol, Master/Slave side).


1.4 (May 26, 2017)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B” and “C”.
•	Fix GPIO as interrupt sampling issue. Now trigger times can be observed in every fetch.
•	Fix performance issue on SPI Slave Receiving and GPIO receiving.
•	FT4222_I2CMaster_WriteEx can send 65531 bytes in one transition (previous is 508 bytes) 


1.3 (Aug 8, 2016)
Maintenance release.

Release Fixes

•	Support Chip version “A”, “B” and “C”
•	Add API FT4222_I2CSlave_SetClockStretch/FT4222_I2CSlave_SetRespWord.
•	Add API FT4222_SPISlave_Init_Ex
•	SPI Master provide CLK_2 option.
•	interrupt status can be read by FT4222_GPIO_Read and FT4222_GPIO_ReadTriggerQueue


1.2 (Aug 24, 2015)
Maintenance release.

Release Fixes

•	Support Chip version “A” and “B” 
•	add API I2CMaster ReadEx/WriteEx/GetStatus


1.1 (Sep 4, 2014)
Maintenance release.

Release Fixes

•	Support Chip version “A” 

