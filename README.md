#  First, the principle of the algorithm 

##  1. PCA-based initial registration 

   Principal Component Analysis (PCA) is a commonly used data analytics method, which extracts the main characteristic components of the data through linear transformation, and is often used for latitude reduction of high latitude data. The initial registration method based on principal component analysis mainly uses the principal axis direction of the point cloud data for registration. First, calculate the covariance matrix of two sets of point clouds, and calculate the main characteristic components according to the covariance matrix, that is, the principal axis direction of the point cloud data; then calculate the rotation matrix through the principal axis direction, and calculate the movement of the center coordinates of the two sets of point clouds directly to obtain the translation vector. The process of PCA principal component analysis method for initial registration is as follows: Assume the sum of two sets of point clouds, and the number is, respectively. First calculate the centers of the two sets of point clouds -,; then calculate their covariance matrices - and; by performing Singular Value Decomposition (SVD) on the sum, the eigenvectors of the two can be obtained -,. Here, is the 3x3 matrix, which is the main direction of the sum of the two sets of point clouds. Then calculate the initial rigid body transformation parameter () through formula (4), where is the initial rotation matrix, which is the initial translation vector.  

##  2. RT initial correction 

   The initial rotation matrix and translation vector are obtained by principal component analysis. Due to the possibility of reverse in the main axis direction, the obtained initial sum may not be used for fine registration. If the error of the point cloud after initial registration is large, the exact alignment will converge in the wrong direction, resulting in the inability to perform correct registration. Therefore, before fine registration, it is necessary to complete the correction of the initial value. First, the point cloud is rotated and translated using the uncorrected initial value and formula (5). By searching for the nearest point, the corresponding point set (number N) in the point cloud is found, and the error of the initial registration is calculated using formulas (6) and (7), where the error between the first corresponding point is the average mean square error of the two point clouds. The 3x3 matrix is the main direction of the point cloud to be registered, and the three column vectors extracted are the three axis directions of X, Y, and Z respectively. Find the direction opposite to the main axis of the target point cloud, and invert the column vectors corresponding to the opposite direction. That is, since the directions of the three axes of X, Y, and Z are both forward and reverse, there are a total of 8 cases of corresponding transformation. Calculate the initial value corresponding to these 8 cases, which corresponds to the minimum hour, which is the correct initial conversion parameter. The 8 cases corresponding to the main axis are shown in Table 1. 

   By inverting the column vector of, a new main direction can be found, and the initial sum after correction can be obtained by using formula (4), and then the two sets of point clouds can be rotated to a roughly coincident position by using formula (5) to provide an initial value for subsequent accurate registration. 

##  3. References 

>  [1] Bellekens B , Spruyt V , Berkvens R , et al. A survey of rigid 3D pointcloud registration algorithms[C]// Ambient: the Fourth International Conference on Ambient Computing. 2014. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574496091
  ```  
#  III. Display of results 

 ![avatar]( 20210403183536493.png) 

 The test data used in this paper: Open3D algorithm test data.rar   

#  IV. C++ Edition 

 PCA implements point cloud coarse registration (C++ version) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  First, the code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574449286
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574449286
  ```  


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

   The PCL :: PF HEs timation fast point feature histogram calculation function is implemented in. For the specific calculation process, see: Open3D calculation FPFH feature. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574486225
  ```  
#  III. Display of results 

 ![avatar]( ff70ed9c8ba84b54b027dc573257d1b3.png) 



--------------------------------------------------------------------------------

#  I. Overview 

   The calculation function of PCL :: PFH Estimation Point Feature Histogram is realized in. [Point Cloud Local Feature Descriptor] PFH & FPFH 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574469044
  ```  
#  III. Display of results 

 ![avatar]( 4030ae96a38e41f19959653baf0137c8.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 References 

>  [1] doc: Estimating VFH signatures for a set of points [2] PCL: pcl :: VFH Estim a tion [3] Ma Zhijun, Yang Junyou, Sun Yizhen. Research on object recognition based on multi-feature fusion [J]. Science and Technology and Innovation, 2021 (16): 33-35. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957441386
  ```  
#  III. Display of results 

 ![avatar]( fbb8ca86cb8e4f90a5465a4795ca339a.png) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  Introduction to use 

   Knowing the index of a point, to extract the point from the original point cloud data, an index extractor is required to achieve it, and the application range of the index extractor is very wide. 

##  1. Main function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
>  Provides a pointer to an index vector representing the input data. 

##  2. Define the index 

 Method one 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
>  Vector class of type int 

 Method two 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
>  A null smart pointer to the vector class of type int 

 Method three 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
 The range representation of the region of interest (not commonly used, mostly used for ordered point clouds, but do not need to be understood.) 

##  3. Use of indexes 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
#  Code example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574476582
  ```  
#  III. Display of results 

 ![avatar]( a5da523012cb4d4f8c71400e9e174162.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Theoretical basis 

 The idea of this algorithm is as follows: 

##  2. Implementation process 

   Aleksey Golovinskiy et al. proposed a point cloud segmentation method based on minimum cut. In 3D point cloud data, a K-nearest neighbor graph is established according to an approximate position of the object, and the foreground constraint or optional background constraint is forced to be added, and then the minimum cut is found to complete the segmentation of the foreground and background. Object segmentation in 3D point clouds is challenging, the real-world data is relatively noisy, the foreground and background points are often entangled, and the point cloud data obtained by scanning is unevenly distributed. Existing point cloud segmentation methods mainly focus on extracting geometric data and local point cloud data, and rarely perform object segmentation. The method based on image cutting was originally applied in image foreground and background segmentation, but now the method is extended to process 3D point cloud data, but it lacks information such as color or texture for reference, does not exist smooth surface model and also contains noise points. Given the approximate position of an object, the purpose of the segmentation algorithm is to return the former attractions belonging to the object. In addition, in order to improve efficiency and accuracy, depending on the size of the object, a horizontal radius parameter belonging to the foreground range needs to be attached. The algorithm is divided into five steps: 

##  3. References 

>  [1] doc: Min-Cut Based Segmentation [2] Link to original paper: Min-Cut Based Segmentation of Point Clouds [3] PCL: pcl :: MinCut Segmentation [4] Liu Chuncheng. Columnar target change detection based on point cloud data [D]. Beijing University of Civil Engineering and Architecture, 2018.p37-38 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574418761
  ```  
#  III. Display of results 

 ![avatar]( e531e52f62c741269026b1e11f4ab8c2.png) 



--------------------------------------------------------------------------------

#  First, the principle of MLS 

##  1. Overview 

>  Original English paper: Surfaces Generated by Moving Least Squares Methods Related literature: [1] Zeng Qinghong, Lu Detang. Curve and surface fitting based on moving least squares method [J]. Journal of Engineering Graphics, 2004 (01): 84-89. [2] Wei Ya, Xiao Yong, Yan Chuang, Liu Yalin, Wang Linbing. Optimization of pavement 3D reconstruction data based on point cloud preprocessing [J]. Journal of Jilin University (Engineering Edition), 2020, 50 (03): 987-997.pcl :: Moving Least Squares massive point cloud data processing theory and technology [Cheng Xiaojun, Jia Dongfeng, Cheng Xiaolong edited] 2014 edition, this book has a detailed description of the principle of moving least squares. 

##  2. Moving least squares method 

   The moving least squares method fits a moving least squares surface to the neighborhood of each sampling point, and calculates the normal vector and curvature of the sampling point based on the information of the local surface. It is usually divided into 3 steps to calculate: Step 1: Calculate the local approximate hyperplane. The local approximate hyperplane is = {}, where the normal vector of the hyperplane is the neighborhood point of the point, so that the following nonlinear energy function should be minimized: Among them, it is a monotonically decreasing positive weight function, which is usually taken as the global estimation of the sampling space distance. It can control the smoothness of the moving least squares surface, which can be dynamically taken as the radius of the surrounding sphere of the point K neighborhood. Step 2: Least squares fitting. Use the local quadric surface to fit the local point cloud. Suppose it is the orthogonal projection to the top, its local two-dimensional coordinates, and its height above can make the following errors, minimum: Step 3: Get the point corresponding to the point on the moving least squares surface. Usually, the normal direction of the hyperplane estimated in the first step is used as the normal direction of the sampling point. Because the moving least squares estimation normal direction is obtained by nonlinear optimization, the method is more accurate. Comparing the covariance analysis method with the moving least squares method, the covariance analysis method is not as accurate as the moving least squares method, but the computational efficiency is greatly improved, and it is more suitable when the point cloud scale is large. The moving least squares method improves the estimation accuracy on the basis of sacrificing efficiency, and is more suitable when the point cloud scale is small or the estimation accuracy of the point cloud normal vector and curvature has higher requirements. 

##  3. References 

>  [1] Lancaster, P. and K. Salkauskas. “Surfaces generated by moving least squares methods.” Mathematics of Computation 37 (1981): 141-158. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574465722
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574465722
  ```  
>  Failed to find match for field'rgb '. Because PointXYZRGB () is used, and the raw point cloud data entered does not contain rgb information. 

 ![avatar]( 96648113184147f68cd010ae24ae3f8a.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm principle 

 ![avatar]( 3f8881a746274881b5d7fb06e8d27e4a.png) 

##  2. Algorithm steps 

 ![avatar]( 9d250b19da284398b9081bd2671c6fd1.png) 

##  3. References 

>  [1] Yang Xu. Filtering and segmentation processing of lidar point cloud data [D]. Harbin Institute of Technology, 2020. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574423202
  ```  
#  III. Display of results 

##  1. Primitive point cloud 

 ![avatar]( 062d1f8d2f0b482985410de60c40e39e.png) 

##  2. Segmentation results 

 ![avatar]( 0b99eeb8649a4c348b866af61c0a3b7e.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm overview 

   Greedy projection triangulation is to maintain a list of points from which a mesh can be grown and expand it until all possible points are connected. It can handle disordered points from one or more scans as well as with multiple connected parts. It works best if the surface is locally smooth and there is a smooth transition between areas with different point densities. 

##  2. References 

>  Fast triangulation of unordered point clouds 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574475500
  ```  
#  III. Display of results 

 ![avatar]( 54d4b57cc4e84ff68059d7fa3d0a4af1.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Overview of the principle 

   Specify the number of sampling points to obtain a fixed number of points from the point cloud. 

##  2. References 

>  [1] Faster Methods for Random Sampling 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574451281
  ```  
#  III. Display of results 

 ![avatar]( 08b1e3dae4dd45ea99426ea349d81b61.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 ![avatar]( 470ff5836f904858922d3caf490f6e10.png) 

##  References 

>  [1] Wang Shaochen. Research on the measurement method of workpiece curved surface contour based on point cloud reconstruction technology [D]. Shandong University, 2020. p: 29~ 30 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574449135
  ```  
#  III. Display of results 

##  1. Primitive point cloud 

 ![avatar]( 0f5876794bab43e981b75bedd42c6e8f.png) 

##  2. Visualize the classification results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574449135
  ```  
 ![avatar]( 6ce5d455d863432d9e5c7693381094c7.png) 

##  3. Classify and save the results 

 ![avatar]( 6afeca64c7a54c44a3cc61c80345f2c5.png) 



--------------------------------------------------------------------------------

#  First, the surface curvature 

    In this case, the curvature used refers to the surface curvature calculated from the eigenvalues of the point cloud. The definition is as follows: If the eigenvalues of any little bit are satisfied, the surface curvature of the point is: the smaller the flatter the neighborhood, and the larger the fluctuation of the neighborhood. The change process from small to large is shown in the visualization result as: the gradual change process of red, yellow, green and blue. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574463530
  ```  
#  III. Display of results 

 ![avatar]( 49c0989a7716437e9b29608e41f518b3.png) 



--------------------------------------------------------------------------------

#  First, simple visualization 

   CloudViewer is a straightforward, simple point cloud visualization designed to view point clouds with as little code as possible. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( b3d08e8c4db0438e8a2224262a6a194d.png) 

#  Display the color characteristics of the point cloud itself 

   PointCloudColorHandlerRGBField requires that the point cloud type contains three color components of RGB, that is, the method directly displays the RGB attribute field information of each point in the point cloud, rather than displaying different colors by coloring the point cloud. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( 6691b4cc66694cb898a0841446107257.png) 

#  Three, custom point cloud color characteristics 

   PointCloudColorHandlerCustom works with any format point cloud, it is not required that the point cloud type contain three RGB color components, that is, the point cloud with id "sample cloud" is colored as a whole. The value range of custom RGB colors is [0,255] 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( e607128b1a404a309050f284064fdbb1.png) 

#  Fourth, distinguish the depth by color 

   PointCloudColorHandlerGenericField display different depth values as different colors to achieve the purpose of distinguishing the depth by color; the difference of the point cloud according to the depth value ("x", "y", "z" can be used) is implemented as a code of different colors as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( f14e3005ba2340cf80d404a85d2f66b8.png) 

#  V. Intensity rendering 

   PointCloudColorHandlerGenericField < PointT > extracts 1D data using fields given by the user and displays colors at each point using a min-max look up table. The implementation code is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( 5bbbae4fa48b4cc8919c19c5bcef755d.png) 

#  Curvature rendering 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574452156
  ```  
 ![avatar]( 79efa3c53de7445db7d3681185acb8a4.png) 



--------------------------------------------------------------------------------

#  Reflection intensity 

    The point cloud data obtained by lidar has not only the three-dimensional geometric information of the object surface, but also the reflection intensity information. The three-dimensional geometric information of the laser point cloud data is the key data for three-dimensional reconstruction, and the reflection intensity information can reflect the differences between different objects and the differences of different colors of the same object to a certain extent, reflecting the characteristics of texture. In recent years, there have been more and more applications of laser point cloud reflection intensity data, such as point cloud feature extraction based on reflection intensity information, point cloud registration, ground object classification, point cloud segmentation and point cloud filtering. In general, the ratio of laser reflection energy to laser emission energy is called laser reflection intensity. 

#  Second, intensity display 

    The intensity display in pclpy is slightly different from that in traditional cognition. For example, the difference in the covering materials of surface objects will lead to different performance values of the reflection intensity information of point clouds. Roads in cities are mostly covered with asphalt, and the reflectivity is lower. Compared with other features, the point clouds of roads are mostly black on the reflection intensity map, but red in the intensity rendering results of pclpy. 

#  III. Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574466690
  ```  
#  IV. Display of results 

 ![avatar]( dd26d486c1a14f2db5afe5f67046bbb9.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 See: [1] pclpy RANSAC fitting segmented cylinder [2] pclpy projection filter - point cloud projected onto fitted plane 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428339
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574428339
  ```  
 ![avatar]( 430bf68967b24540b7336c2c72b9b0ab.png) 



--------------------------------------------------------------------------------

#  I. Overview 

   There are countless blogs on the Internet that use RANSAC for cylinder fitting, so I will not introduce the principle here. The code in this article is implemented in python. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574421909
  ```  
#  III. Display of results 

 ![avatar]( 8d97dbe78ec944ac9c1d5069e3fa7337.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  model coefficient 

   The linear equation has three representations: general, point-to-point, and parametric. PCL uniformly adopts the point-to-point equation, and the point-to-point equation of the straight line is: where, direction vector, known points. Used to determine the line model, the six coefficients of the line are given by the points on the line and the direction of the line: [point_on_line point_on_line point_on_line line_direction x line_direction y line_direction] 

##  4. References 

>  [1] pcl :: SampleConsensusModelLine [2] Bao Jianqiang, Zhang Xianzhou, Li Yuan, Xiao Yuanmiao, Chen Xiao, Luo Chao. Application analysis of various spatial straight line fitting methods [J]. Science of Surveying and Mapping, 2020, 45 (05): 132-139 + 151. 

#  Code implementation 

##  1. Implementation method 1 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574444635
  ```  
##  2. Implementation method 2 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574444635
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574444635
  ```  
 ![avatar]( abb753b544b34c7887c54cd793213111.png) 



--------------------------------------------------------------------------------

