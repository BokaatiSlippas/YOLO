# YOLO


Notes: For each grid cell we have 5B+n elements
B is bounding box number i.e. how many objects we can detect per grid cell

5 because for each B we have x,y for centre of grid cell, sqrt(h), sqrt(w) and probability C of having object in the box

n because that is how many classes we have, i.e. probability of class a given object exists in the grid cell
