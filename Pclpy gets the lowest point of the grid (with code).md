#  First, the principle of the algorithm 

##  1. Introduction to the algorithm 

>  Point cloud voxelization is a more common processing method for point clouds. VoxelGrid and ApproximateVoxelGrid voxelization methods, the first of which is to obtain the point cloud center of gravity in each grid by dividing the voxel grid as the point cloud representative of the grid. The second is to represent the point cloud of the grid according to the center point of the grid. The GridMinimum class is to divide the three-dimensional point cloud into the grid in the X-Y plane, and then find the point with the smallest Z coordinate in each grid to represent the grid. If the grid does not have a point cloud, it will not generate a center point to represent the grid point cloud as ApproximateVoxelGrid. 

##  2. Applicability 

>  GridMinimum can effectively filter the situation where the elevation information is discontinuous, such as vehicles parked under trees, etc., which can effectively find the lowest point and prepare for subsequent segmentation. However, if there are no vehicles under the tree or the ground point cannot be scanned, then the point of the grid may be the lowest point of the scanned leaves, which requires further processing. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574463485
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574463485
  ```  
 ![avatar]( e41956b242cf49c296c962914f4ab0ec.png) 

