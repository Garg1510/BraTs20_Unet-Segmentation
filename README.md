# BraTs20_Unet-Segmentation

Data Loading and Preprocessing:

The code loads MRI images (T1, T1c, T2, and FLAIR) from the BraTS 2020 dataset using the nibabel library. It normalizes the images using MinMaxScaler to ensure pixel values are scaled between 0 and 1.

Image Mask Adjustment:

The segmentation mask is loaded, and the pixel values are adjusted to reassign the value '4' to '3' to simplify the classification into four categories (0, 1, 2, 3). This is important for consistent labeling in the segmentation task.

Visualization:

Random slices from the processed images and their corresponding masks are displayed using matplotlib. This allows for a visual inspection of the image quality and the mask alignment.

Data Combination and Cropping:

The code combines the FLAIR, T1c, and T2 images into a single multi-channel numpy array. It then crops the combined images and masks to a specific size (128x128x128x4) to ensure they are suitable for further processing, particularly for creating 3D patches.

Patch Extraction and Saving:

The script iterates over the list of images, processes each one by combining and cropping, and checks if the mask has enough non-zero labels (at least 1% useful volume). Valid images and their masks are saved as numpy arrays for future use, ensuring that only useful data is retained for training the model. 
