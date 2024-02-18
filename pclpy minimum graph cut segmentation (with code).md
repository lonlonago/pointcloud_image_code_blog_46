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

