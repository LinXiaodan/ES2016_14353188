����cartographer
=================
###��װ
####������64λϵͳ 16GB�ڴ�(����8Gò��Ҳ��) Ubuntu 14.04 (Trusty) gcc version 4.8.4

####1����װwstool ��rosdep
	sudo apt-get update
	sudo apt-get install -y python-wstool python-rosdep ninja-build
####2�����������ռ�catkin_ws������
	mkdir catkin_ws
	cd catkin_ws
	wstool init src
####3���ϲ�cartographer_ros.rosinstall�ļ�����ô�������
	wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall
	wstool update -t src

####4����װdeb dependencies��������
	rosdep init
	rosdep update
	rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
####5��build֮��װ
	catkin_make_isolated --install --use-ninja
	source install_isolated/setup.bash
###��������
####1������2Dʾ����
	wget -P ~/Downloads https://storage.googleapis.com/cartographer-public data/bags/backpack_2d/cartographer_paper_deutsches_museum.bag
####2��	��������2Dʾ��
	roslaunch cartographer_ros demo_backpack_2d.launch bag_filename:=${HOME}/Downloads/cartographer_paper_deutsches_museum.bag
####3����ý����ʾ����
https://github.com/LinXiaodan/ES2016_14353188/tree/master/images/car.png