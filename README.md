# Apple_Plant_Disease_Detection

Plant Disease Detection is one of the mind-boggling issues that exists when we talk about using Technology in Agriculture. Although research has been done to detect whether a plant is healthy or diseased using Deep Learning and with the help of Neural Networks, new techniques are still being discovered.

Here is my approach for Detecting whether a plant leaf is healthy or unhealthy by utilising classical Machine Learning algorithms and pre-processing the data using Image Processing.

# Dataset

The dataset used for this project has been taken from Plant-Village- Dataset which can be found here 
https://github.com/spMohanty/PlantVillage-Dataset/tree/master/raw/color.

The data employed in this project has been obtained from the "colour" directory in the "raw" folder of the GitHub Repository. Specifically, the dataset used for modelling purposes focuses on images of Apple Leaves. This dataset is structured into two main folders for training purposes: "Diseased" and "Healthy." The "Diseased" folder encompasses images of leaves affected by various ailments such as Apple Scab, Black Rot, or Cedar Apple Rust. In contrast, the "Healthy" folder contains photos of vibrant and disease-free green leaves, each appropriately labelled.

# Image Properties
Type of File: JPG File.

Dimensions: 256 * 256.

Width: 256 Pixels.

Height: 256 Pixels.

Horizontal Resolution: 96 dpi.

Vertical Resolution: 96 dpi.

Bit Depth: 24.

# Steps Involved
Data Preprocessing:

1) Loading Original Images: A total of 800 images are provided for each class, Diseased and Healthy, and are used as input for the machine.

2) Converting Images from RGB to BGR: Since OpenCV, the Python library for Image Processing, accepts images in the BGR (Blue, Green, Red) colouring format, the images are converted from RGB to the original BGR format.

3) Converting Images from BGR to HSV: This conversion is necessary because HSV separates the luma (image intensity) from chroma (colour information), which is valuable in various applications. For instance, if you intend to perform histogram equalization on a colour image, you typically want to apply it only to the intensity component while preserving the colour components. In computer vision, separating colour components from intensity is often required for reasons such as handling lighting changes and eliminating shadows. It's worth noting that HSV is just one of several colour spaces that separate colour from intensity (others include YCbCr, Lab, etc.). HSV is commonly used because readily available code for converting between RGB and HSV exists and is easy to implement.

4) Image Segmentation for Color Extraction: To isolate the leaf from the background, segmentation is performed, and the colour of the leaf is extracted from the image.

5) Applying Global Feature Descriptors: Global features are extracted from the image using three feature descriptors:

- Color: Color channel statistics (mean, standard deviation) and colour histograms.
- Shape: Hu Moments, Zernike Moments.
- Texture: Haralick Texture, Local Binary Patterns (LBP).

After extracting these features from the images, they are combined using the numpy function "np.stack."

6) Label Encoding: The labels for the images in the folder are encoded numerically to facilitate machine understanding.

7) Dataset Splitting: The dataset is divided into training and testing sets in an 80/20 ratio.

8) Feature Scaling: Feature scaling is employed to standardize independent features within the data to a fixed range. This preprocessing step handles variations in magnitudes, values, or units. Min-Max Scaler is used, which scales values between 0 and 1.

9) Saving Features: Once the features are extracted from the images, they are saved in an HDF5 file. HDF5 (Hierarchical Data Format version 5) is an open-source file format designed to support large, complex, and heterogeneous data. HDF5 uses a file directory-like structure to organize data within the file.

10) Modeling: The model is trained using seven machine learning models:

- Logistic Regression
- Linear Discriminant Analysis
- K Nearest Neighbors
- Decision Trees
- Random Forest
- Naïve Bayes
- Support Vector Machine

Validation is performed using a 10-fold cross-validation technique.

11) Prediction: The model with the best performance is then trained on the entire dataset, and its accuracy is evaluated on the testing set using the "Predict" function.

A high accuracy of 97% is achieved using the Random Forest Classifier.

# Files Info

Utils: Contains Python file for conversion of labels of images in the train folders.

Code_Notebook: Contains .ipynb for the Plant Disease Detection.

Output: Contains training labels and data 

Testing Notebook: Contains Detailed Specifications of Functions applied in the leaf images.
