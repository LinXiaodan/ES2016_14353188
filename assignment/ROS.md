��װROS
===============

###1������sources.list
	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

###2������keys
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

###3����װ
####ȷ����������������µ�
	sudo apt-get update
####��װDesktop-Full
	sudo apt-get install ros-kinetic-desktop-full
####��װDesktop
	sudo apt-get install ros-kinetic-desktop
####��װROS-Base
	sudo apt-get install ros-kinetic-ros-base

###4����ʼ��rosdep
	sudo rosdep init
	rosdep update

###5�����û���
	echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
	source ~/.bashrc

###6����װrosinstall
	sudo apt-get install python-rosinstall

