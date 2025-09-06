# YOLO


Notes: For each grid cell we have 5B+n elements
B is bounding box number i.e. how many objects we can detect per grid cell

5 because for each B we have x,y,sqrt(h),sqrt(w),C

(x,y) for offset from the top-left corner of the grid cell itself
h and w for the height and width of the object region
C for the probability that there is an object in the region

+n because that is how many classes we have, i.e. probability of class a given object exists in the grid cell
