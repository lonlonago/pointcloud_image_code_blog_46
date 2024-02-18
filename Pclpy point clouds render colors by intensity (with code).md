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

