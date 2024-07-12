DETECTION OF DOWN SYNDROME FROM MEASUREMENT OF NUCHAL TRANSLUCENCY ASSESSMENT IN ULTRASOUND IMAGES USING U-NET MODEL

Reference Paper: https://ieeexplore.ieee.org/abstract/document/10493220

Overview:

This repository contains the implementation of a deep learning model for the identification of Down Syndrome, specifically Trisomy 21, using ultrasound images. The model utilizes YOLOv8 for region identification, UNet for segmentation of the nuchal fold tissue, and OpenCV (CV2) for measuring the Nuchal Translucency (NT).

YOLOv8 Implementation:

1. Ultralytics YOLOv8 is used for region identification in ultrasound fetus images.
2. Five variants of YOLOv8 are available: nano(n), small(s), medium(m), large(l), and extra large (x).
3.	Data is loaded into Roboflow Ultralytics for training the YOLOv8 model.
4.	913 images are used for training, 260 for validation, and 414 for testing with one class labelled as NT.

UNet Model for Segmentation:

1.	UNet is employed for the first phase of segmentation to measure NT.
2.	The model is enhanced in the output layer and feature extraction of the image.
3.	UNet is a CNN network consisting of encoder and decoder blocks, made up of convolution layers and pooling.
4.	Masks of the images are created using ImageJ in '.tif' format.
5.	The model architecture includes lossless feature connections and pixel-by-pixel categorization.

CV2 for NT Measurement:

1.	OpenCV (CV2) is used for measuring NT, where masks of the images play a crucial role.
2.	Image thresholding techniques are employed for visualization of predicted masks.
3	NumPy and the Python Imaging Library (PIL) module are used for image data processing.
4.	OpenCV transforms the RGB image to grayscale for viewing the expected mask.
5.	Binary thresholding is utilized to create a binary mask of the region of interest.
6.	Centroid coordinates of the region of interest are obtained for further analysis.

Training and Evaluation:

1.	Adam optimizer is used for iterative optimization during model training.
2.	Sparse Categorical Cross Entropy is chosen as the loss function for multi-class segmentation.
3.	The model is compiled and evaluated using the 'accuracy' metric.
4.	Training involves iterating over the dataset for a set number of epochs while controlling batch size.

Measurement Analysis:

1.	Pertinent features within the delimited areas are analyzed after obtaining predicted masks.
2.	Line masks are created to highlight specific edges or features in the image.
3.	Euclidean distance formula is used to compute distances between detected locations.
4.	Distances are reported in millimeters using known DPI values, providing insights into dimensional characteristics.

Requirements:

1.	Python 3.x
2.	PyTorch
3.	OpenCV (CV2)
4.	NumPy
5.	PIL (Python Imaging Library)
   
Results:

1.	YOLOv8 achieves accurate region identification in ultrasound images.
2.	UNet provides precise segmentation of the nuchal fold tissue.
3.	CV2 accurately measures the Nuchal Translucency (NT) for prenatal screening.
