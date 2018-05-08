# chaowei_Navigation
For ChaoWei navigation simulation.

%%
平台：Ubuntu14.04、ROS-indigo
采用Gmapping/amcl，完成导航巡检
%%

1. 任意位置建立工作空间，载入源代码，编译
$ mkdir navigation_ws
$ git clone https://github.com/Frankie94/chaowei_Navigation.git
$ mv chaowei_Navigation src
$ catkin_make

2. 在Gazebo界面载入机器人世界
(在工作空间navigation_ws下)
$ source devel/setup.bash
$ roslaunch diff_wheeled_robot_gazebo diff_wheeled_gazebo_full.launch

3. 使用Gmapping建图
$ source devel/setup.bash
$ roslaunch diff_wheeled_robot_gazebo gmapping.launch

4. 使用amcl定位
$ source devel/setup.bash
$ roslaunch diff_wheeled_robot_gazebo amcl.launch

5. 使用rviz可视化结果
$ source devel/setup.bash
$ rosrun rviz rviz
在rviz界面左下角点击'add'，在'By display type'中添加'RobotModel'，在'By topic'中添加'/map/Map'，'/global_costmap/Map'，'/local_costmap/Map'。
点击                   按钮在未知地图上选一点，机器人会自主导航至该点。

如果采用键盘控制：
将以上3/4/5替换为：
$ source devel/setup.bash
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
$ rosrun rviz rviz 
