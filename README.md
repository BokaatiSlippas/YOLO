# YOLO


Notes: For each grid cell we have 5B+n elements
B is bounding box number i.e. how many objects we can detect per grid cell

5 because for each B we have x,y,sqrt(w),sqrt(h),C

(x,y) for offset from the top-left corner of the grid cell itself
h and w for the height and width of the object region
C for the probability that there is an object in the region (Confidence)

+n because that is how many classes we have, i.e. probability of class a, given object exists in the grid cell

x and y are 0 to 1 proportion of the grid cell

w and h are proportion of the entire image

We select a box if the IoU (Interesection/Union) is greater than a selected threshold

Loss equation: L = L_class + L_localisation

L_class = sum over all grid cells i with objects actually present (sum over all classes c ((probability of c in i) - ground truth)^2)

L_localisation = L_confidence + L_coord

