# yolov8_ros
完整的在ROS下实现YOLOV8
cd ~/catkin_ws/src

# 下载功能包

git clone https://github.com/Gaofan666/Yolov8_ros.git

# 更新ultralytics和weights

现在我们要替换两个东西，一个是ultralytics文件夹，这个ultralytics是80.0.92版本的比较旧，直接删掉即可。去yolov8官网下载最新版的ultralytics或者替换自己的文件夹放进来

git clone https://github.com/ultralytics/ultralytics.git

用到哪个python解释器就在哪个虚拟环境装一下rospkg，比如我用的虚拟环境是yolov8，运行以下命令：

conda activate yolov8

pip install rospkg

修改yolov8_ros/scripts/yolo_v8.py，文档开头的 /usr/bin python 替换为yolov8虚拟环境的解释器的位置。

#!/home/hhh/.conda/envs/yolov8/bin/python3.8

# 更改图像话题和权重文件路径

修改yolov8检测的图像话题在/Yolov8_ros/yolov8_ros/launch/yolo_v8.launch文件中

cd ~/catkin_ws

catkin_make

source devel/setup.bash

roslaunch usb_cam usb_cam-test.launch

roslaunch yolov8_ros yolo_v8.launch
