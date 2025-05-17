## PyTorch3D Mesh Deformation Project:
Taking inspiration from the signature "Ornithopter" featured in the Dune series, I am applying skillsets gained from the Educative course 3D Machine Learning with PyTorch3D ; 
this project deforms the mesh of a 3D dragonly model based on the mesh of an Ornithopter using a differentiable rasterizer. Vertices and vertex colors are initialized as learnable parameters and are updated using torch optimizers (experimented with SGD and ADAM so far)

Sample mesh deformations are provided below:

<img width="350" alt="image" src="https://github.com/user-attachments/assets/b379bb12-1d69-4539-b172-16be18ba77c9" />
<img width="350" alt="image" src="https://github.com/user-attachments/assets/c9f837e2-aa25-47d2-b600-a56cd0871923" />
<p align="center">
  <img width="245" alt="image" src="https://github.com/user-attachments/assets/6504a96f-59c6-40bb-b941-ed85357acce9" />
</p>

The source mesh (dragonfly) consists of 26,809 vertices and the target mesh (Ornithopter) consists of 1,206,181 vertices. To make the two meshes more compatible I implemented vertex upsampling using the PyTorch3D SubdivideMeshes Class and vertex downsampling using the trimesh simplify_quadric_decimation function.

The start point 3D models were sourced from BlenderKit: <br />
Artist credits: <br />
Marinko Tambur: https://www.blenderkit.com/asset-gallery-detail/22b280a9-e03a-423d-a114-8a41d9869033/  <br />
<img width="500" alt="image" src="https://github.com/user-attachments/assets/bf1a849a-e7de-4385-a559-105ab48a776e" /> <br />
^ a sample of the Ornithopter renders from training data <br /> <br />
DDD:  https://www.blenderkit.com/get-blenderkit/362e45ed-9ec5-4416-9cd6-72f418333569/  <br />
<img width="500" alt="image" src="https://github.com/user-attachments/assets/7b57985a-99a1-45ba-bd75-804061038686" /> <br />
^ a sample of Dragonfly renders from training data



The source and target meshes are rendered from multiple angles to create a training dataset.

A weighted combination of the following losses are used to update the mesh:
- Mesh edge loss
- Mesh Laplacian smoothing
- Mesh normal consistency
- MSELoss

The deformed mesh can be exported as a .obj file (using the function save_mesh_as_obj) ready for further work in blender.
<img width="800" alt="image" src="https://github.com/user-attachments/assets/33ec261e-e3cb-4a05-825a-096dc33822e0" /> <br />
^ the deformed mesh successfully loaded into blender <br />

I am fascinated by the meshes that I am able to capture during the training process - below is an iteration from this process, blended with a dystopian background:
<img width="809" alt="image" src="https://github.com/user-attachments/assets/ec4f37fd-a1f9-426e-8b58-8e4253703dea" />








