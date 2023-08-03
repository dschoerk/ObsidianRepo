![[Pasted image 20230803154405.png|500]]
- Skeleton-based
- Contour-based
- Volume-based [[@tuVoxelPoseMulticamera3D2020|Hanyue2020]]


## Challenges for 3D HPE

### Low availability of data
Recording data is difficult. To measure 3D joint locations multi camera setups are required. Observing a joint from multiple views allows for triangulation of the exact 3D joint location. 

Semi-supervised methods: [[@liBoostingSingleFrame3D2019|Li2019]]


### Surface vs Joint location

Small neural network to correct for the difference between surface and joint location: DepthFix [[Reading Notes/@martinEvaluationDifferentMethods2021|Martin2019]]


### Temporal stability 

http://dx.doi.org/10.1109/CVPR.2019.00351
https://doi.org/10.1109/GCCE50665.2020.9292014
[[Reading Notes/@pavllo3DHumanPose2019|VideoPose3D]]

### Person-centric coordinates
"Most of the methods focus on single persons,  which estimate the poses in the person-centric coordinates, i.e., the coordinates based on the center of the target person. Hence,  these methods are inapplicable for multi-person 3D pose estimation, where the absolute coordinates (e.g., the camera coordinates) are  required." -  [[@chengDualNetworksBased2023|Cheng2023]]

### Occlusions
[[@fabbriLearningDetectTrack2018|Fabbri2018]]



## Datasets

3D: 
Human3.6M http://vision.imar.ro/human3.6m/description.php
MPI-INF-3DHP https://vcai.mpi-inf.mpg.de/3dhp-dataset/
HumanEva-I&II Datasets http://humaneva.is.tue.mpg.de/
CMU Panoptic Dataset http://domedb.perception.cs.cmu.edu/ 
MuPoTS-3D: https://vcai.mpi-inf.mpg.de/projects/SingleShotMultiPerson/
JTA: https://aimagelab.ing.unimore.it/imagelab/page.asp?IdPage=25 (virtual)

2D: 
Penn Action http://dreamdragon.github.io/PennAction/











