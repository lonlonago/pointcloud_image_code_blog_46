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

