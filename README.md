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

#### Image files
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

## 001-Demosiacing
<img src="images/001-Demosaicing-1.png" alt="Manual Demosaic" width="400"/>

### Objective
The objective of this section is to 
- extract the raw image info from .dng file and visualize what each pixel value looks like without color info
- perform a manual demosaicing on a 100x100 sample and compare to the post-processed image already stored in .dng file
- exploring different demosaicing methods: bilinear, edge-aware interpolation, Gradient-based demosaicing, deep learning-based demosaicing (e.g., PyTorch, OpenCV DNN)


<img src="images/001-demosaicing-raw.png" alt="Manual Demosaic" width="400"/>

#### Bayer layer info (rawpy)
The first step in performing demosaicing is to get the Bayer layer info. I used rawpy to access the Bayer layer (there are other methods too). The output returns a 2x2 matrix whose values map to RGB colors: 0=Red, 1=Green, 2=Blue, 3=Green, so the [[0 1],  [3 2]] return in our case means it is RGGB Bayer layer. This is the standard colormapping for Libraw. More details can be found here: https://www.libraw.org/docs/API-overview.html#cfa

### Bilinear Demosaicing 
The out for the Bilinear demosaicing kernel compared OpenCV demosaicing and rawpy demosaicing. The difference in colors is due to auto WB and CCM applied to rawpy vs the other two methods.
<img src="images/001-Demosaicing-output.png" alt="Manual Demosaic" width="1200"/>


















