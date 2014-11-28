Generating the meshes
=====================

NOTE: the meshes are in [mm]


1. Scanning
-----------

Equipment: [Turntable and Konica](http://sensing.konicaminolta.us/products/vivid-910-3d-laser-scanner/)

Procedure: A scan was ran for each object for each object pose. The angle step depends on the geometry and material. The smaller the better the longer the processing time. The issue was to have overlapping in the object to easy the registration/merging. The files generated are in folder "unregistered_scans (raw)".


2. Registering and merging
--------------------------

Software: 

Procedure1: Align each scan for a single object pose. It worked fine with almost default parameters for most objects. The files generated in this step are in folder "registered_scans"

Procedure2: Merge all registered scans of a single pose into a single mesh. It worked with default parameters for most objects. The files generated are in folder "merge_of_registered_scans"

Procedure3: Merge all merges of registered scans into a single mesh. The registration needed information introduced by the user before merging. It worked with default parameters for most objects. The files generated are in folder "merge_of_merges".


3. PLY, STL and PCD (downsample)
--------------------------------

Software: [Meshlab](http://meshlab.sourceforge.net/)

Procedure: Filter -> Remeshing, simplification, and reconstruction -> Quadric Edge Collapse Decimation -> around 10000 to 15000 faces, then export meshes as PLY with normals, and STL, both in binary.

Software: [PCL utilities](http://www.pointclouds.org/)

Procedure: `pcl_ply2pcd mesh.ply mesh.pcd`

At least my version of the conversor has this bug, I had to edit manually the field names "nx ny nz" by "normal_x normal_y normal_z" for a correct visualization, which can be checked by running `pcl_viewer -normals 1 -normals_scale 1 mesh.pcd`


4. Virtual Scanning (for some objects)
--------------------------------------

Software: [PCL utilities](http://www.pointclouds.org/)

Procedure: 
```
pcl_virtual_scanner -object_coordinates 1 -single_view 0 -view_point 1000,0,0 -organized 0 -noise 1 -noise_std 0.5 mesh.ply
```
