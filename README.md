# image-colorizer


A tool that automatically colorizes black and white images using deep learning. This project uses a pre-trained Caffe model based on the work by Zhang et al. to add realistic colors to grayscale photographs.

## Features

- Automatic colorization of black and white images
- Uses deep learning (CNN) for realistic color prediction
- Supports JPEG image format
- Easy-to-use command-line interface

## Requirements

- Python 3.x
- OpenCV (cv2)
- NumPy

## Installation

1. Clone or download this repository

2. Install the required Python packages:
```bash
pip install opencv-python numpy
```

3. **Download the pre-trained model:**
   
   The model file is too large for GitHub, so you need to download it separately:
   - Download from: [colorization_release_v2.caffemodel](https://www.dropbox.com/s/dx0qvhhp5hbcx7z/colorization_release_v2.caffemodel?dl=1)
   - Place the downloaded file in the `model/` folder

## Project Structure

```
image-colorizer/
│
├── colorize.py                           # Main script
├── model/
│   ├── colorization_deploy_v2.prototxt   # Model architecture
│   ├── colorization_release_v2.caffemodel # Pre-trained weights (download separately)
│   └── pts_in_hull.npy                   # Cluster centers
└── README.md
```

## How to Run

1. **Navigate to the project directory:**
   ```bash
   cd image-colorizer
   ```

2. **Run the colorization script:**
   ```bash
   python colorize.py -i path/to/your/image.jpg
   ```
   
   Replace `path/to/your/image.jpg` with the actual path to your black and white JPEG image.

### Example

```bash
python colorize.py -i images/old_photo.jpg
```

## Controls

- After running the script, two windows will appear showing the original and colorized images
- Press any key to close the windows and exit the program

## Supported Image Formats

- JPEG (.jpg, .jpeg)
- Other formats supported by OpenCV (PNG, BMP, etc.)

## How It Works

1. The script loads a pre-trained deep neural network model
2. Your input image is converted to LAB color space
3. The L (lightness) channel is fed into the neural network
4. The network predicts the AB (color) channels
5. The channels are combined and converted back to BGR for display

## Troubleshooting

**"Image not found" error:**
- Check that the image path is correct
- Use absolute paths if relative paths don't work
- Ensure the image file exists and isn't corrupted

**"Model not found" error:**
- Make sure you've downloaded the `.caffemodel` file
- Verify it's placed in the `model/` folder
- Check that the file name matches exactly: `colorization_release_v2.caffemodel`

**Module import errors:**
- Install missing packages: `pip install opencv-python numpy`

## Credits

This project is based on the colorization algorithm by:
- Richard Zhang, Phillip Isola, and Alexei A. Efros
- "Colorful Image Colorization" (ECCV 2016)

## License

This project uses a pre-trained model. Please refer to the original authors' licensing terms for the model weights.
