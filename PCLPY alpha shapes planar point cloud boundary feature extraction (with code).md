#  First, the principle of the algorithm 

##  1. Overview of the principle 

 ![avatar]( 20210324113107628.png) 

   In the experiment of extracting boundary points from planar point clouds, the alpha shapes algorithm proposed by Edelsbrunner H is a simple and effective algorithm for extracting boundary points quickly. It overcomes the shortcomings of the influence of the shape of point cloud boundary points, and can quickly and accurately extract boundary points. Its principle is as follows: As shown in the figure below, for a plane point cloud of any shape, if a circle of radius is, roll around it. If the radius of the rolling circle is small enough, each point in the point cloud is a boundary point; if it is appropriately increased to a certain extent, it only rolls on the boundary point, and its rolling track is the point cloud boundary.  

##  2. Detailed process 

 ![avatar]( 20210324113442723.png) 

   The specific algorithm steps are as follows: (1) For any point, the radius of the rolling circle is searched for all points within the distance point in the point cloud, which is recorded as the point set; (2) Select any point, and calculate the coordinates of the center of the circle according to the coordinates of these two points.  

 The center of the circle is the coordinate of the center of the circle in two cases where the radius is equal to two points. The coordinate calculation formula is shown in (1):     

 among them 

   (3) After removing the points in the point set, calculate the distance from the remaining points to the points respectively. If the distance from all points to or points is greater than that, it indicates that the point is a boundary point. (4) If the remaining point-to-point or point-to-point distances are all greater than that, then all points in the point set are rotated as points. If there is a point that satisfies the conditions (2) (3), it indicates that the point is a boundary point, terminates the judgment of the point, and determines the next point. If there is no such point in all the nearest neighbors, it indicates that the point is a non-boundary point. 

##  3. References 

>  [1] LIU Ke. Research on Boundary Extraction Algorithm of Planar Point Cloud [D]. Changsha University of Science and Technology, 2017. P51-53 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574487779
  ```  
#  III. Display of results 

 ![avatar]( fa70060ac0e34c6fbdadaffebe5137e6.png) 

