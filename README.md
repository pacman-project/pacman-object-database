pacman-object-database
======================

Models of IKEA objects to be used within the project.

1. `laser_scanner_db` Generated using a 3D laser scanner (only depth information): `laser_scanner_db`

2. `asus_scanner_models` Generated using an RGB-D camera (Asus Xtion Pro) and turn-table. Color and depth informations are available, within point clouds. Generated meshes are without color information.
	- discontinued
3. `inhand_scanner_models` Generated using the in-hand scanner software and Asus Xtion Pro. Each object has: 
        - Point cloud with color and normals in pcd format.
        - Full processed mesh with color and normals in Collada format.
        - Full processed mesh in binary STL.
