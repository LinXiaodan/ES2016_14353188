安装ROS
===============

###1、设置sources.list
	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

###2、设置keys
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

###3、安装
####确定软件包索引是最新的
	sudo apt-get update
####安装Desktop-Full
	sudo apt-get install ros-kinetic-desktop-full
####安装Desktop
	sudo apt-get install ros-kinetic-desktop
####安装ROS-Base
	sudo apt-get install ros-kinetic-ros-base

###4、初始化rosdep
	sudo rosdep init
	rosdep update

###5、设置环境
	echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
	source ~/.bashrc

###6、安装rosinstall
	sudo apt-get install python-rosinstall

