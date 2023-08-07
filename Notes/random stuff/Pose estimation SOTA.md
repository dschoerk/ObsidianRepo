- 2D -> 3D Lifting
- Direct regression
- Probability maps
- Pose and shape estimation

"In this section, we review state-of-the-art works on 3D human pose estimation from still [RGB images](https://www.sciencedirect.com/topics/engineering/rgb-image "Learn more about RGB images from ScienceDirect's AI-generated Topic Pages").

**Lifting 2D to 3D.** Depth regression from 2D is an ill-posed problem where several 3D poses can be projected to the same 2D [joints](https://www.sciencedirect.com/topics/engineering/joints-structural-components "Learn more about joints from ScienceDirect's AI-generated Topic Pages"). Atrevi _et al._ [[17]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0017) assign 3D joints from a dataset by 2D body silhouette matching, while Chen and Ramanan [[18]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0018) show that copying depth from 3D mocap data can provide a fair estimation when a nearest 2D matching is given. However, Moreno [[19]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0019) shows that distance of random pairs of poses has more ambiguity in Cartesian space than [Euclidean distance](https://www.sciencedirect.com/topics/engineering/euclidean-distance "Learn more about Euclidean distance from ScienceDirect's AI-generated Topic Pages") matrix. Recent works show that directly using simple [[20]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0020) or cascade [[21]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0021) [MLP](https://www.sciencedirect.com/topics/computer-science/multilayer-perceptron "Learn more about MLP from ScienceDirect's AI-generated Topic Pages") networks can be more accurate. Additionally, 2D joints can be wrongly estimated, making previous solutions sub-optimal. Yang _et al._ [[22]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0022) use adversarial training and benefit from available 3D data along with 2D data to infer depth information. In our case, the proposed denoising [autoencoder](https://www.sciencedirect.com/topics/computer-science/autoencoder "Learn more about autoencoder from ScienceDirect's AI-generated Topic Pages") is used to lift 2D pose to 3D in the lack of paired image and 3D ground truth data.

**Direct regression** refers to regressing 3D pose directly from an RGB image. Due to the nonlinear nature of the human pose, 3D pose regression without modeling correlation of joints is not a trivial task. Brau and Jiang [[23]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0023) estimate 3D joints and camera parameters without direct supervision on them. Instead, they use several loss functions for projected 2D joints, bone sizes and independent Fisher priors. Sun _et al._ [[24]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0024) propose a compositional loss function based on relative joints with respect to a defined kinematic tree. They separate 2D joints and depth estimation in the loss. We avoid relying on such complex losses by using 3D joints and landmarks as intermediate representation.

**Probability maps** are joints likelihood computed for each pixel/volume. From 2D joint heatmaps different solutions are applied to infer the third dimension. Tome _et al._ [[25]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0025) iteratively minimize a function based on 2D belief map and a learnt 3D model to find the most likely 3D pose. Since probability maps are dense predictions, fully [convolutional networks](https://www.sciencedirect.com/topics/computer-science/convolutional-network "Learn more about convolutional networks from ScienceDirect's AI-generated Topic Pages") are usually applied. Luo _et al._ [[26]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0026) extend stacked hourglass (SHN) [[4]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0004) to estimate 2D joint heatmaps along with limb orientation map in each stack. Pavlakos _et al._ [[27]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0027) extend SHN to output 3D [volumetric](https://www.sciencedirect.com/topics/engineering/volumetrics "Learn more about volumetric from ScienceDirect's AI-generated Topic Pages") data by a coarse-to-fine architecture where at each stack the third dimension is linearly increased with 2D heatmaps. Nibali _et al._ [[28]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0028) propose marginal heatmaps from different axis viewpoints.

**Pose and shape estimation.** In order to compute a detailed body model, it is common to estimate body volume or [mesh](https://www.sciencedirect.com/topics/engineering/meshes "Learn more about mesh from ScienceDirect's AI-generated Topic Pages") along with 3D pose. Early proposals were mainly based on the combination of simple geometric objects [[29]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0029), [[30]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0030), while recent approaches are PCA-based [parametric models](https://www.sciencedirect.com/topics/computer-science/parametric-model "Learn more about parametric models from ScienceDirect's AI-generated Topic Pages") like SMPL [[6]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0006). Bogo _et al._ [[7]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0007) were the first to apply SMPL for body pose and [shape recovery](https://www.sciencedirect.com/topics/computer-science/shape-recovery "Learn more about shape recovery from ScienceDirect's AI-generated Topic Pages"). Their method was based on regular [optimization procedures](https://www.sciencedirect.com/topics/engineering/optimisation-procedure "Learn more about optimization procedures from ScienceDirect's AI-generated Topic Pages") given an objective function with several constraints, minimizing projected joints and pre-estimated 2D joints. Such a complex function design is critical for the success of optimization procedures, since SMPL is a many-to-one function and sensitive to noise. Lassner _et al._ [[12]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0012) extended the previous work by including a bi-directional distance between projected mesh and body silhouette. Recent works embed SMPL within deep models. Tung _et al._ [[31]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0031) regressed SMPL pose and shape along with camera parameters. They trained the model with supervision on synthetic data and fine-tuned without supervision at inference time using 2D joints, silhouette and motion losses. Similarly, Kanazawa _et al._ [[9]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0009) regressed as well SMPL and camera parameters, but in addition, they applied adversarial training. Predictions are fed to a [discriminator](https://www.sciencedirect.com/topics/engineering/discriminator "Learn more about discriminator from ScienceDirect's AI-generated Topic Pages") network which classifies them as real/fake with respect to real body scans. Similar to our work, [[8]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0008), [[13]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0013), [[32]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0032) estimate pose and shape parameters from intermediate information, like body segments [[13]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0013), 2D joint heatmaps and body mask [[8]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0008) or 3D joints [[32]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0032). They include SMPL to obtain 3D joints and mesh which are used to compute the loss either in 2D (back-projected from 3D) or 3D. However, this process is ill-posed and sub-optimal because of the loss of depth information (in the case of [[8]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0008), [[13]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0013)) or the ambiguity in joint orientations and shape parameters (in the case of [[32]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0032)). We show 3D joints and surface landmarks can better deal with this problem outperforming aforementioned solutions. Recently, Varol _et al._ [[14]](https://www.sciencedirect.com/science/article/pii/S0031320320302752#bib0014) proposed a multi-tasking approach to estimate body 2D/3D pose, pixel segments and volumetric shape. They use SMPL to generate ground truth body volumes and do not embed SMPL function within the network." - Madadi, Meysam et al. “SMPLR: Deep learning based SMPL reverse for 3D human pose and shape recovery.” _Pattern Recognit._ 106 (2020): 107472.



## SMPL Resources

list of SMPL datasets https://www.youtube.com/watch?v=bVRXPO0Uv0g&t=952s

introduction to SMPL https://smpl-made-simple.is.tue.mpg.de/ 

TransPose https://xinyu-yi.github.io/TransPose/ Pose from inertial sensors

![[Pasted image 20230804112557.png]]
T: Template, J: Joints, W: vertice weights from joints, beta: bodyshape, theta: pose 
allows to learn corrections under different poses, standard skinning suffers e.g. from candy wrapper effect

Example of T_F(beta, theta) change of template due to pose https://youtu.be/rzpiSYTrRU0?t=3549

![[Pasted image 20230804111918.png]]
idea is factorization of 3d model into "pose" and "identity"

SMPL body model


![[Pasted image 20230804111614.png]]
Estimate SMPL parameters from images

![[Pasted image 20230804111752.png]]
Extension of smplify to face and hands

![[Pasted image 20230804111428.png]]

![[Pasted image 20230804111357.png]]
MANO hand model

![[Pasted image 20230804111224.png]] DECA, Learning animatable detailed 3d face model from in-the-wild images, feng et al., siggraph 2021

![[Pasted image 20230807092654.png]]
https://expose.is.tue.mpg.de/, source: https://youtu.be/lNTmHLYTiB8?t=228
Expose: estimate SMPL with neural networks


![[Pasted image 20230804113256.png]]
[Gül Varol](https://imagine.enpc.fr/~varolg/), [Ivan Laptev](http://www.di.ens.fr/~laptev/) and [Cordelia Schmid](https://thoth.inrialpes.fr/~schmid/), [Andrew Zisserman](https://www.robots.ox.ac.uk/~az/), _Synthetic Humans for Action Recognition from Unseen Viewpoints_, IJCV 2021.

![[Pasted image 20230804113656.png]]
"On the Benefits of 3D Pose and Tracking for Human Action Recognition", CVPR 2023


![[Pasted image 20230804120742.png]]Kim, Seong-heum and Donghyeon Cho. “Viewpoint-Aware Action Recognition Using Skeleton-Based Features from Still Images.” _Electronics_ 10 (2021): 1118.


![[Pasted image 20230804120910.png]]
Saqlain, Muhammad et al. “3DMesh-GAR: 3D Human Body Mesh-Based Method for Group Activity Recognition.” _Sensors (Basel, Switzerland)_ 22 (2022): n. pag.


"Total Capture: A 3D Deformation Model for  
Tracking Faces, Hands, and Bodies"
https://www.cs.cmu.edu/~hanbyulj/totalcapture/
Video shows examples for very subtle motion for assembly and playing musical instruments. Comparison of ADAM and frankmocap. 


