# Copy-Move Forgery Detection Using SIFT, DBSCAN, and DeepLabV3

## Project Overview

With the widespread use of digital images in communication, social media, and forensic applications, ensuring the integrity and authenticity of visual content is critical. Copy-move forgery is a common manipulation technique where image regions are copied and pasted within the same image. This project explores a robust approach to detect such forgeries using:

1. **SIFT (Scale-Invariant Feature Transform)** for detecting keypoints and descriptors.
2. **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** for clustering matched keypoints.
3. **DeepLabV3** for precise segmentation of forged regions.

### Key Contributions

- **SIFT**: Detects distinctive keypoints invariant to scale, rotation, and partial affine transformations, ideal for identifying copied and pasted regions.
- **DBSCAN**: Reduces false positives by clustering keypoints and identifying dense regions of matches.
- **DeepLabV3**: Provides semantic segmentation for precise localization of forged patches.
- **Dataset**: The CoMoFoD (Image Database for Copy-Move Forgery Detection) dataset is used for evaluation.

## Methodology

### 1. Preprocessing
- Convert the input image to grayscale as SIFT operates on intensity values rather than color.

### 2. Feature Detection and Matching
- Apply **SIFT** to detect keypoints and compute descriptors.
- Use **FLANN-based matcher** (Fast Library for Approximate Nearest Neighbors) to match descriptors within the same image.
- Apply **Lowe's ratio test** to filter reliable matches and reduce false positives.

### 3. Clustering Matches
- Use **DBSCAN** to cluster the matched keypoints.
- Define thresholds for cluster size and minimum required matches to identify copy-move regions.

### 4. Forgery Segmentation
- Crop detected regions and pass them through **DeepLabV3** for semantic segmentation.
- Integrate the segmented patches into the original image to create a complete forgery map.

### 5. Visualization
- Draw rectangles around detected regions and visualize the connections between matched keypoints.
- Include the original image, forgery mask, and segmented results for clarity.

## Results
The algorithm was applied to 200 images from the CoMoFoD dataset. Examples of both high-performing and less successful results are provided for better understanding. The method demonstrates performance comparable to modern techniques for simple images in the dataset.
