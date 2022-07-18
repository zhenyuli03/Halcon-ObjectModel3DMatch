# Halcon 三维点云匹配实现无序抓取


## 实现点云无序抓取需要知道目标物体的位置和姿态(pose)x,y,z,rx,ry,rz

在Halcon里边，实现点云匹配方法有很多，主要有基于表面的匹配，基于形状的匹配

1.基于表面的点云匹配操作较为简单，可实现类似于2D模板匹配的输出，参考例程:find_surface_model.hdev
2.基于形状的点云匹配，准备的工作貌似比较复杂，需要把匹配物体的模型建从来再进行匹配，从而估算出物体的姿态，参考：create_shape_model_3d_lowest_model_level.hdev

基于表面的匹配核心算子
1.创造模板：create_surface_model
2.寻找模板：find_surface_model


需要注意的是，创建模板时需要把自己的基准面去掉，只保留识别的物体。
寻找模板时也一样，去掉基准面，找模板后会输出姿态，随后用rigid_trans_object_model_3d进行三维的刚体变换
显示即可

调整最大的识别物：在算子find_surface_model里genparamName把'num_matches',把genparamValue填入你的匹配个数
例：find_surface_model (SFM, ObjectModel3DSelectPiont, 0.05, 0.1, 0.2, 'true', 'num_matches', 10, Pose, Score, SurfaceMatchingResultID)
# Halcon-ObjectModel3DMatch
# Halcon-ObjectModel3DMatch
# Halcon-ObjectModel3DMatch
