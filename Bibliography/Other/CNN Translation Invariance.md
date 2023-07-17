

On Translation Invariance in CNNs: Convolutional Layers can Exploit Absolute Spatial Location

https://openaccess.thecvf.com/content_CVPR_2020/papers/Kayhan_On_Translation_Invariance_in_CNNs_Convolutional_Layers_Can_Exploit_Absolute_CVPR_2020_paper.pdf

CNNs are assumed to be translation invariant. The paper shows that this is not necessarily the case due to boundary constraints. Depending on how boundaries are handled in convolution layers, the translation invariance can be improved. 

thoughts:
It could be interesting to further experiment with translation invariance in the context of action recognition. In Action Recognition architectures with 3D convolutions are used to inhibit the temporal dependencies between images. If CNNs were translation invariant this shouldn't be working that well on the temporal domain. In the temporal domain we want to utilize the sequential nature of video frames, rather than shuffling them. In the spatial domain it depends on the observed actions if translation invariance is important. 

