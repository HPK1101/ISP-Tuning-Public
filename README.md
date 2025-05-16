### ISP-Tuning (Public Version) 

Created the ISP-Tuning repository for:
- Demonstrate understanding of core ISP blocks
- Create a modular ISP pipeline to learn how each ISP block works
- Practice ISP Tuning on raw data 

### Planned ISP block to be included

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
### Scripting and code development Process
- For the development process, I use the local folder on Windows to keep the raw files. Installing the GitHub Desktop application seems the easiest way I found.
- The script development is on Colab and online, then the files will be downloaded locally and pushed to GitHub using the GitHub Desktop app.

### Google Drive folder for raw files
- TBD for public access (WIS)

### working with .DNG files
Key Structure of a .DNG File (TIFF-based structure)

![image](https://github.com/user-attachments/assets/91fe5b74-1350-41f6-a3ad-6540325df52d)
<p align="center">
  <img src="your-image-path.png" width="100"/>
</p>


TIFF --> Header	Describes byte order, version
IFD0 --> Basic info: width, height, color layout
EXIF --> ISO, shutter speed, aperture, timestamp
CFA Pattern --> 	Tells you the sensor’s Bayer layout (e.g., RGGB)
ColorMatrix1/2 -->	Used for converting to XYZ or sRGB
Raw Data --> Sensor pixel values (one color per pixel)
Thumbnail -->	Quick embedded JPEG for previews
  
### License
- MIT License
