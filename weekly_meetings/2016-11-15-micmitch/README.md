# DC resistivity survey design using octree meshes

Presented by: [Michael Mitchell](https://github.com/micmitch)

[![2016-11-16](https://img.youtube.com/vi/0_e60fEAma4/0.jpg)](https://youtu.be/0_e60fEAma4)

## Summary

A discussion of recent sensitivity based survey design work for tunnel based DC resistivity surveys.
I start out showing the limitations of a simple linear array of electrodes to constrain the around tunnel
location of conductive or resistive structures and then show the benefits of using ring arrays. The survey
design aspect comes in when we try to determine which measurements in the much larger ring array survey are
actually required to adequately sample the region of interest (ROI) around the tunnel. Due to the large number
of cells required to model a 3m square tunnel on a tensor mesh I discuss recent work which has been done to
make use of the octree mesh class in SimPEG. DC forward modelling currently work on octree meshes using a CC
discretization and homogeneous Dirchlet BC. Work is on going to improve the efficiency of interpolation on the
octree meshes and hook them up with the regularization for inversion.




