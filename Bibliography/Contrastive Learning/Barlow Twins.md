Found in https://lilianweng.github.io/posts/2021-05-31-contrastive/

![[Pasted image 20220325122420.png]]

"Barlow twins" is a contrastive learning approach where two distorted (augmented) images are fed through the same network. Optimally, both networks should produce the same response. The idea is to compute the cross-correllation between the responses and drive it closer to the identity matrix. As such, the correllation between different features is minimized. 