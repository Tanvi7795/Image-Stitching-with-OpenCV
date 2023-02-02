# Panorama-Stitching-with-OpenCV
## Given a pair of images that share some common region, the goal of this project is to “stitch” them and create a panoramic image scene using Python and OpenCV. 

Image stitching or photo stitching is the process of combining multiple photographic images with overlapping fields of view to produce a segmented panorama image. It is important to note that both images need to share some common region.

## Specification 
Throughout this article, we go over some of the most famous Computer Vision techniques. These include:
* Keypoint detection
* Local invariant descriptors (SIFT, SURF, etc)
* Feature matching
* Homography estimation using RANSAC
* Perspective warping

### Keypoing detection
Keypoints are found by calculating the difference of Gaussian blur of the image at different levels. Then those images are subtracted from each other resulting in the difference of images with different levels of Gaussian blurs. The resultant images are stacked upon each other to look for extreme points which are locally distinct, those are keypoints. 

### Local invariant descriptors 
Descriptors are computed by looking at the neighborhood of the keypoint, breaking down the local neighborhood into small areas, and then computing the gradient in these small areas.

### Feature matching 
With OpenCV, feature matching requires a Matcher object. Here, we explore two flavors:
* Brute Force Matcher
* KNN (k-Nearest Neighbors)

### Homography estimation using RANSAC 
RANdom SAmple Consensus or RANSAC is an iterative algorithm to fit linear models. Different from other linear regressors, RANSAC is designed to be robust to outliers. It turns out that the Homography is very sensitive to the quality of data we pass to it. Hence, it is important to have an algorithm (RANSAC) that can filter points that clearly belong to the data distribution from the ones which do not.

### Perspective warping 
Once we have the estimated Homography, we need to warp one of the images to a common plane. Here, we are going to apply a perspective transformation to one of the images. Basically, a perspective transform may combine one or more operations like rotation, scale, translation, or shear. The idea is to transform one of the images so that both images merge as one.
