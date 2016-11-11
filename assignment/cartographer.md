配置cartographer
=================
###安装
####环境：64位系统 16GB内存(本文8G貌似也行) Ubuntu 14.04 (Trusty) gcc version 4.8.4

####1、安装wstool 和rosdep
	sudo apt-get update
	sudo apt-get install -y python-wstool python-rosdep ninja-build
####2、创建工作空间catkin_ws并进入
	mkdir catkin_ws
	cd catkin_ws
	wstool init src
####3、合并cartographer_ros.rosinstall文件，获得代码依赖
	wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall
	wstool update -t src

####4、安装deb dependencies（依赖）
	rosdep init
	rosdep update
	rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
####5、build之后安装
	catkin_make_isolated --install --use-ninja
	source install_isolated/setup.bash
###运行样例
####1、下载2D示例包
	wget -P ~/Downloads https://storage.googleapis.com/cartographer-public data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag
####2、	启动测试2D示例
	roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag
####3、获得结果显示如下
https://github.com/LinXiaodan/ES2016_14353188/tree/master/images/car.png