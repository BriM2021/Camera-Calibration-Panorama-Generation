# Panorama-Generation

This project involves generating a panorama by stitching together multiple images from a dataset. The steps outlined below will guide you through the key stages of the process, starting from feature detection to multi-image stitching.

## Steps:

### 1. Keypoint Detection 
- Extract keypoints and descriptors from the first two images using the **SIFT (Scale-Invariant Feature Transform)** algorithm.  
- SIFT is a feature detection algorithm that identifies distinctive points in images and computes descriptors that are invariant to scaling, rotation, and affine transformations.  
- Visualize the keypoints by drawing them overlaid on the original images to verify the accuracy of the detection.

### 2. Feature Matching  
- Match the extracted features between the two images using two different algorithms:  
  a) **Brute-Force Matching**: Compares each descriptor from the first image with every descriptor from the second image.  
  b) **FLANN-Based Matching**: A more efficient method that uses an approximate nearest-neighbor search for faster matching.  
- After performing the matching, display the matched features by drawing lines connecting corresponding keypoints in both images.

### 3. Homography Estimation 
- Compute the **Homography Matrix** using **RANSAC (Random Sample Consensus)**.  
- RANSAC is an iterative method that helps estimate the transformation between two images by identifying the best-fitting model while minimizing the influence of outliers.  
- The homography matrix will be used to align the two images in preparation for panorama stitching.

### 4. Perspective Warping  
- Use the computed homography matrices to warp the two images into a new perspective.  
- The warped images will be aligned side-by-side, simulating how the images would appear if viewed from a common viewpoint.  
- Display these warped images without any cropping or blending as the next step will involve combining them.

### 5. Image Stitching  
- Stitch the two warped images together to form the final panorama.  
- Initially, display the panorama without any cropping or blending.  
- In the second display, apply cropping and blending to remove any unwanted artifacts and achieve a seamless panorama.

### 6. Multi-Image Stitching   
- Extend the stitching process to handle multiple images from the dataset.  
- Perform stitching for all images in the folder to create a comprehensive panorama.  
- Display the final stitched panorama as the culmination of the multi-image stitching process.  
- **Hint**: Reuse the stitching functions developed in the previous steps for consistency.
