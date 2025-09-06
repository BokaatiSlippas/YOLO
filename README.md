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

L_localisation = L_coord + L_conf

L_coord = lambda_coord * (sum over all grid cells i (sum over all bounding boxes j where cell i and box j is responsible for the object (l)))

$l = \left( \sqrt{w_i} - \sqrt{\hat{w}_i} \right)^2 + 
    \left( \sqrt{h_i} - \sqrt{\hat{h}_i} \right)^2 + 
    (x_i - \hat{x}_i)^2 + 
    (y_i - \hat{y}_i)^2$

square differences between prediction and ground truth

L_conf = sum over all grid cells i (sum over all bounding boxes j where cell i and box j is responsible for the object (l))

$L_{loc} = L_{conf} + L_{coord}$


$L_{conf} = \sum_{i=0}^{S^2} \sum_{j=0}^B 
\left[ \mathds{1}_{ij}^{obj} (C_i - \hat{C}_i)^2 \right] +
\lambda_{noobj} \sum_{i=0}^{S^2} \sum_{j=0}^B \left[ \mathds{1}_{ij}^{noobj} (C_i - \hat{C}_i)^2 \right]$


% Coordinate Loss (L_coord)
\[
L_{coord} = \lambda_{coord} \sum_{i=0}^{S^2} \sum_{j=0}^B \mathds{1}_{ij}^{obj}
\left[
(x_i - \hat{x}_i)^2 + (y_i - \hat{y}_i)^2 + \left( \sqrt{w_i} - \sqrt{\hat{w}_i} \right)^2 + \left( \sqrt{h_i} - \sqrt{\hat{h}_i} \right)^2
\right]
\]

