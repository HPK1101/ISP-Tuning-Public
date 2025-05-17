# ISP-Tuning (Public Version) 

## Intro 

Created the ISP-Tuning repository for:
- Demonstrate understanding of core ISP blocks
- Create a modular ISP pipeline to learn how each ISP block works
- Practice ISP Tuning on raw data 

#### Planned ISP block to be included

- dead/hot pixel removal
- Demosaicing
- White Balance
- Color Correction
- color space conversion
- Tone Mapping & Gamma correction
- Noise Reduction
- Sharpening
- Lens Shading Correction
- 3A - Auto Exposure 
- 3A - Auto White Balance
- 3A - Auto-Focus (focus compute)
- 
#### Scripting and code development Process
- For the development process, I use the local folder on Windows to keep the raw files. Installing the GitHub Desktop application seems the easiest way I found.
- The script development is on Colab and online, then the files will be downloaded locally and pushed to GitHub using the GitHub Desktop app.

#### Raw files
- Were downloaded from https://data.csail.mit.edu/graphics/fivek/
- initially started using a .DNG file from my Iphone and then noticed there is no Bayer layer info for the image

#### Working with .DNG files
Key Structure of a .DNG File (TIFF-based structure)
- TIFF --> Header	Describes byte order, version
- IFD0 --> Basic info: width, height, color layout
- EXIF --> ISO, shutter speed, aperture, timestamp
- CFA Pattern --> 	Tells you the sensor’s Bayer layout (e.g., RGGB)
- ColorMatrix1/2 -->	Used for converting to XYZ or sRGB
- Raw Data --> Sensor pixel values (one color per pixel)
- Thumbnail -->	Quick embedded JPEG for previews
  
#### License
- MIT License


## Demosiacing

#### Bayer layer info
- I used rawpy to access the Bayer layer (there are other methods too)
- 0=Red, 1=Green, 2=Blue, 3=Green, so the [[0 1],  [3 2]] return means it is RGGB Bayer layer. This is the standard colormapping for Libraw. More details can be found here: https://www.libraw.org/docs/API-overview.html#cfa
