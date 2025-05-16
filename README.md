<p align="center">
  <img width="1000" alt="image" src="https://github.com/user-attachments/assets/1be7217e-0b19-4b26-9f63-f1e08d2ae5cd" />
</p>

## PyTorch3D Mesh Deformation Project:

This project deforms the mesh of a 3D dragonly model based on the mesh of an Ornithopter using a differentiable rasterizer. Vertices and vertex colors are initialized as learnable parameters and are updated using torch optimizers (experimented with SGD and ADAM so far)

Sample mesh deformations are provided below:

<img width="450" alt="image" src="https://github.com/user-attachments/assets/b379bb12-1d69-4539-b172-16be18ba77c9" />
<img width="450" alt="image" src="https://github.com/user-attachments/assets/c9f837e2-aa25-47d2-b600-a56cd0871923" />
<p align="center">
  <img width="245" alt="image" src="https://github.com/user-attachments/assets/6504a96f-59c6-40bb-b941-ed85357acce9" />
</p>

The source mesh (dragonfly) consists of 26,809 vertices and the target mesh (Ornithopter) consists of 1,206,181 vertices. To make the two meshes more compatible I implemented vertex upsampling using the PyTorch3D SubdivideMeshes Class and vertex downsampling using the trimesh simplify_quadric_decimation function.

The 3D models were sourced from BlenderKit: <br />
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

(The header image for this README are a collection of Ornithopter vertices rendered using PyTorch3D)







