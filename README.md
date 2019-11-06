# pgm2dng
# PGM to DNG command line converter

pgm2dng is a command line converter, that converts pgm files with raw CFA data into DNG format, that could be processed with raw processors (Adobe Camera Raw, Raw Therapee, Fast CinemaDNG Processor). Usually we get raw frame from machine vision or industrial camera as a bitmap of 8/10/12/14/16-bit values which we store as PGM (Portable Gray Map) image. Apart from bitmap we know bit depth and image resolution (width and height) for every frame. But this is not enough for good color reproduction.. For raw processor to correctly work with resulting DNGs we also should provide some additional information:
* DCP (digital camera profile) file, that contains color transformation information (at least 3x3 color matrix and illuminant information). If you don't have this profile, you can do the follopwing:
	- Try to find sutable profile in the  DCPProfiles folder of this ropsitory.
	- Try to find sutable profile in the internet.
	- If you have DNG file from the camer of the same model, you can use dcptool to decompile it to xml file and compile that xml file into dcp.
	- Create your own profile with DCamProf and color checker. You will need a shot of color checker in linear color space (some camera can shoot in log or other non linear color spaces, so you should switch it to linear mode). To create profile with DcamProf you will have to demosaic (debayer) raw gray image into RGB one. For that purpose one can use fastDebayer freeware application from Fastvideo.
* White point - RGB values of gray patch from color checker or gray card. These values provide correct white balance on processed image. One of the ways to obtain these values is to  demosaic (debayer) raw gray image into RGB one. For that purpose one can use fastDebayer freeware application from Fastvideo. Then open this image into graphics editor (Photoshop or GIMP) and get these values with color picker.
* CFA (bayer) pattern. This information is required for color processor to correctly convert gray raw to RGB image.

## Usage
pgm2dng.exe command-line options: --in=< path/to/input/file >  --out=< path/to/output/file >--dcp=< path/to/dcp/file >  --wp=< R,G,B > --white=< white >  --black=< black >  --compress<br>

Where: 

  --in=< path/to/input/file > - path to pgm file (mandatory). 8, 10, 12, 14, 16 bits per pixel PGMs are supported, but 10 bit PGMs are encoded as 16 bit DNGs.<br>
  --out=< path/to/output/file > - path to dng file (mandatory) <br>
  --dcp=< path/to/dcp/file > - path to dcp (digital camera profile) file (mandatory) <br>
  --pattern=< pattern > - CFA pattern. Alowed values: RGGB, GBRG, GRBG, BGGR (mandatory) <br>
  --wp=< R,G,B > - comma separated white point values (mandatory) <br>
  --white=< white > - white level (optional, dafault is maximem for a given bitdepth) <br>
  --black=< black > - black level (optional, default 0) <br>
  --compress - compress image with lossless jpeg <br>

## Compile and build
To build pgm2dng from source you need Visuil C++ 2017. For use with other compiler you should recompile XMP SDK. Currently it is built as a static lib with Visuil C++ 2017, so if you need another compiler you should rebuild it with it and setup your build environment to point to correct lib files.

To build application with Visuil C++ 2017:
* Open pgm2dng.sln file with Visuil Studio 2017
* Set build configuration to Release.
* Select Build\Build solution menu item, or press Ctrl + Shift + B.
* pgm2dng.exe will be placed into bin filder for release build and into src\x64 for debug build.

To tes application run test.cmd from bin folder. This script will process sample 8/10/12/14/16 pgm files from Samples folder with and without lossless jpeg compression.

##Useful links:

Adobe DNG Software Development Kit (SDK) 1.4 - https://www.adobe.com/support/downloads/dng/dng_sdk.html

DCamProf software - https://www.ludd.ltu.se/~torger/dcamprof.html

RawTherapee - http://rawtherapee.com

Fast CinemaDNG Processor - https://www.fastcinemadng.com

Fastvideo Image & Video Processing SDK for CUDA - https://www.fastcompression.com/products/sdk.htm

