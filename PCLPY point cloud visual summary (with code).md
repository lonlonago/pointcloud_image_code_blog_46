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

