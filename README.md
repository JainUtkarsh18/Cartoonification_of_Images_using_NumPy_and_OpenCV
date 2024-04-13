# Cartoonification an Image using OpenCV and NumPy in Python.

This Python project aims to provide a simple and efficient way to cartoonify images using various image processing techniques. By applying a combination of edge detection, color quantization, and image filtering, this project can transform regular images into cartoon-like representations.

# Features

- **Edge Detection**: Detects edges in the input image using techniques like Canny edge detection.
- **Color Quantization**: Reduces the number of colors in the image to create a simplified color palette, resembling cartoonish artwork.
- **Image Filtering**: Applies various image filtering techniques such as bilateral filtering to smooth out colors and enhance the cartoon effect.

# Installation

1. Clone the repository:

   ```
   git clone https://github.com/your_username/cartoonification.git
   ```

2. Navigate to the project directory:

   ```
   cd cartoonification
   ```

3. Install the required dependencies:

   ```
   pip install -r requirements.txt
   ```

# Usage

To cartoonify an image, run the `cartoonify.py` script with the path to the input image as an argument:

```
python cartoonify.py input_image.jpg
```

This will generate a cartoonified version of the input image and save it as `cartoonified_image.jpg` in the same directory.

# Project Processing Sequence
This project workflow is divided into 11 steps.

These steps are also used to maintain an proper processing system of the project.

## Step 1: Importing the required modules.
Import the following modules:

1. **CV2**: Imported to use OpenCV for image processing </br>
2. **easygui**: Imported to open a file box. It allows us to select any file from our system.</br>
3. **Numpy**: Images are stored and processed as numbers. These are taken as arrays. We use NumPy to deal with arrays.</br>
4. **Imageio**: Used to read the file which is chosen by file box using a path.</br>
5. **Matplotlib**: This library is used for visualization and plotting. Thus, it is imported to form the plot of images.</br>
6. **OS**: For OS interaction. Here, to read the path and save images to that path.</br>

## Step 2: Building a File Box to choose a particular file.
In this step, build the main window of application, where the buttons, labels, and images will reside. Also give it a title by title() function.

Explanation:
fileopenbox() is the method in easyGUI module which returns the path of the chosen file as a string. It opens the file box, i.e the pop-up box to choose the file from the device, which opens every time while running the code.
NOTE: Now, all the operation will be done on the button click, thus all the below steps are the part of function cartoonify (ImagePath)

## Step 3: How to store an Image?
For a computer, everything is just numbers. Thus, convert an image into a numpy array.</br>
<ul>
<li> .imread() is a method in cv2 which is used to store images in the form of numbers. This helps to perform operations according to needs. </li>
<li> The image is read as a numpy array, in which cell values depict R, G, and B values of a pixel. Resize the image after each transformation to display all the images on a similar scale at last.</li>
<li> To convert an image to a cartoon, multiple transformations are done. Firstly, an image is converted to a Grayscale image.</li>
<li> Then, the Grayscale image is smoothened, and then try to extract the edges in the image.</li>
<li> Finally, form a color image and mask it with edges. This creates a beautiful cartoon image with edges and lightened color of the original image.</li>
</ul>

## Step 4: Transforming an image to grayscale
cvtColor(image, flag) is a method in cv2 which is used to transform an image into the colour-space mentioned as ‘flag’. Here, first step is to convert the image into grayscale. Thus, use the BGR2GRAY flag. This returns the image in grayscale. A grayscale image is stored as grayScaleImage.</br>

After each transformation, resize the resultant image using the resize() method in cv2 and display it using imshow() method. This is done to get more clear insights into every single transformation step.

## Step 5: Smoothening a grayscale image
To smoothen an image, simply apply a blur effect. This is done using medianBlur() function. Here, the center pixel is assigned a mean value of all the pixels which fall under the kernel. In turn, creating a blur effect.

## Step 6: Retrieving the edges of an image
Cartoon effect has two specialties: Highlighted Edges and Smooth colors.</br>
In this step, For Highlighting edges try to retrieve the edges and highlight them. This is attained by the adaptive thresholding technique.</br>

## Step 7: Preparing a Mask Image
Now, prepare a lightened color image to mask with edges at the end to produce a cartoon image. Use bilateralFilter which removes the noise. It can be taken as smoothening of an image to an extent.</br>

The third parameter is the diameter of the pixel neighborhood, i.e, the number of pixels around a certain pixel which will determine its value. The fourth and Fifth parameter defines signmaColor and sigmaSpace. These parameters are used to give a sigma effect, i.e make an image look vicious and like water paint, removing the roughness in colors. It’s similar to BEAUTIFY or AI effect in cameras of modern mobile phones.

## Step 8: Giving a Cartoon Effect
let’s combine the two specialties. This will be done using MASKING. Perform bitwise and on two images to mask them, thus giving an cartoon effect. Figure_1.png showas all the transitions.

## Step 9: Functionally of save button
Here, the idea is to save the resultant image. For this, we take the old path, and just change the tail (name of the old file) to a new name and store the cartoonified image with a new name in the same folder by appending the new name to the head part of the file.

## Step 10: Make the main window, Make the Cartoonify button in the main window and Make a Save button in the main window.
As the step clear its function. We will create an window to push our image inside the model and save it window for converting it.

## Step 11: Main function to build the tkinter window
Use top.mainloop() for building tkinter window. tkinker window is an platform where all the containers in which all other GUI elements are present.


# Contributions
Contributions to this project are welcome. Feel free to open issues or pull requests with any improvements, bug fixes, or new features.
