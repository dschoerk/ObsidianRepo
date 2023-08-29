![[Pasted image 20230803154405.png|500]]
- Skeleton-based
- Contour-based
- Volume-based [[@tuVoxelPoseMulticamera3D2020|Hanyue2020]] [SMPL model](https://smpl.is.tue.mpg.de/) [STAR model](https://star.is.tue.mpg.de/) [Example videos](https://youtu.be/bVRXPO0Uv0g?t=870)

General note: Lifting from 2D->3D is very common. 

## Challenges for 3D HPE

### Low availability of data
Recording data is difficult. To measure 3D joint locations multi camera setups are required. Observing a joint from multiple views allows for triangulation of the exact 3D joint location. 

Semi-supervised methods: [[@liBoostingSingleFrame3D2019|Li2019]] use video to increase training data



### Surface vs Joint location

Small neural network to correct for the difference between surface and joint location: DepthFix [[Reading Notes/@martinEvaluationDifferentMethods2021|Martin2019]]


### Temporal stability 
Estimating human poses (in 2D or 3D) is typically not temporally stable. Between frames we may observe strange jittering of joint locations. In previous work temporal information from videos was used to create more stable poses over time. 

[[@katoLeveragingTemporalJoint2020|Kato2020]] uses temporal information to resolve depth ambiguity in lifting from 2D to 3D poses
[[Reading Notes/@pavllo3DHumanPose2019|VideoPose3D]] Temporal convolutions over 2D pose keypoints
[[@arnabExploitingTemporalContext2019|Arnab2019]] based on SMPL model



### Person-centric coordinates
"Most of the methods focus on single persons,  which estimate the poses in the person-centric coordinates, i.e., the coordinates based on the center of the target person. Hence,  these methods are inapplicable for multi-person 3D pose estimation, where the absolute coordinates (e.g., the camera coordinates) are  required." -  [[@chengDualNetworksBased2023|Cheng2023]]

### Occlusions
[[@fabbriLearningDetectTrack2018|Fabbri2018]]
[[@wangOCRPoseOcclusionawareContrastive2022]]




## Datasets

3D: 
Human3.6M http://vision.imar.ro/human3.6m/description.php
MPI-INF-3DHP https://vcai.mpi-inf.mpg.de/3dhp-dataset/
HumanEva-I&II Datasets http://humaneva.is.tue.mpg.de/
CMU Panoptic Dataset http://domedb.perception.cs.cmu.edu/ 
MuPoTS-3D: https://vcai.mpi-inf.mpg.de/projects/SingleShotMultiPerson/
JTA: https://aimagelab.ing.unimore.it/imagelab/page.asp?IdPage=25 (virtual)
Shelf/Campus datasets: https://campar.in.tum.de/Chair/MultiHumanPose
SURREAL: ? (virtual)

2D: 
Penn Action http://dreamdragon.github.io/PennAction/




## Software Packages

| Link | Notes |
| - | - |
| https://github.com/openxrlab/xrmocap | Multi-view motion capture from images |
| https://github.com/JunukCha/MultiPerson | Working demo with SMPL |
| https://github.com/vchoutas/smplify-x/ | Difficult setup with many dependencies; didn't run |














