# Camera Calibration Project

This project involves performing camera calibration using a chessboard pattern to estimate the intrinsic and extrinsic parameters of the camera, as well as to study the radial distortion and re-projection errors. The goal is to understand and apply the principles of camera calibration to real-world images captured from a stationary camera.

## Instructions:

1. **Camera Setup**:
   - Place your camera (laptop or mobile phone) stationary on a table.
   - Print out a chessboard calibration pattern (as shown in the tutorials linked below) and stick it on a hard, planar surface.
   - Capture approximately **25 images** of the chessboard pattern in various orientations, ensuring the pattern is fully visible in each image. The pattern should cover all degrees of freedom in terms of rotation and translation. Make sure the corners in the chessboard are automatically detected and correctly identified using OpenCV functions.
   
   - **Links for tutorials**:
     - [Link1](https://learnopencv.com/camera-calibration-using-opencv/)
     - [Link2](https://boofcv.org/index.php?title=Tutorial_Camera_Calibration)

2. **Tasks**:

### 1. **Intrinsic Camera Parameters (5 points)**
   - Report the **estimated intrinsic camera parameters**, which include:
     - **Focal length(s)**
     - **Skew parameter**
     - **Principal point**
   - Include error estimates if available for these parameters.

### 2. **Extrinsic Camera Parameters (5 points)**
   - Report the **estimated extrinsic camera parameters** for each selected image, including:
     - **Rotation matrix**
     - **Translation vector**

### 3. **Radial Distortion Coefficients (5 points)**
   - Report the **estimated radial distortion coefficients** for the camera.
   - Use the radial distortion coefficients to **undistort** 5 of the raw images.
   - Include the original and undistorted images in your report.
   - Observe how straight lines at the corners of the images change after applying the distortion coefficients. Comment briefly on this observation.

### 4. **Re-projection Error (5 points)**
   - Compute and report the **re-projection error** for each of the 25 selected images using the estimated intrinsic and extrinsic parameters.
   - Plot the re-projection error using a **bar chart**.
   - Report the **mean** and **standard deviation** of the re-projection error.

### 5. **Corner Detection and Re-projection (10 points)**
   - Plot figures showing:
     - The corners detected in the original images.
     - The corners after re-projection onto the images for all the 25 images.
   - Comment on how the re-projection error is computed and its significance.

### 6. **Checkerboard Plane Normals (10 points)**
   - Compute the **checkerboard plane normals** (`n_Ci`) for each of the 25 selected images in the **camera coordinate frame of reference** (`Oc`).

---



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
