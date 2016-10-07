DOL配置
======================================

###1、电脑中已经安装好了VMware，在VWware中安装Ubuntu16.0（64位），以下步骤一开始均在/home中

###2、配置C/C++环境
		1）sudo apt-get update		#更新原信息
		> 出现问题：E:Could not lock /var/lib/dpkg/lock -open
		> 可能原因：可能上次安装没正常完成，导致资源被锁
		> 解决方式：将var/lib/apt/liists中的文件全部删掉
		> 			sudo rm /var/cache/apt/archives/lock
		> 			sudo rm /var/lib/dpkg/lock
		> 之后重新开始又出现问题：Err:1 urlA
		> 						Err:2 urlB
		> 						Err:3 urlC
		> 							Temporary failure resolving 'us.archiv.ubuntu.com'
		> 						......
		> 原因：无法连接网站
		> 解决方式：修改DNS
		> 			sudo nano /etc/resolv.conf
		> 			将已有DNS记录使用“#”注释掉，再添加新的DNS记录，如下
		> 				nameserver 8.8.8.8
		> 				nameserver 8.8.4.4
		> 			使用“ctrl+x”保存文件
		> 			锁定文件防止修改DNS
		> 				sudo chattr +i /etc/resolv.conf
		2）sudo apt-get install g++		#安装g++
		> 通过指令验证g++是否安装成功：g++
		> 成功结果：g++: fatal error:no input files
		> 		   compilation terminated
				   
###3、配置java环境
		1）将压缩包jdk-8u40-linux-x64.gz复制到/home下
		2）在/usr/lib下创建文件夹java，将压缩包解压到该文件夹下，重命名为jd8k
			cd /usr/lib
			sudo mkdir java
			sudo tar zxvf /jdk-8u40-linux-x64.gz -C /usr/lib/java
			cd /usr/lib/java 
			sudo mv jdk1.8.0_40/ jdk8
		3）配置环境变量
			在/home中，选择view->Show Hidden Files，打开文件.bashrc
			在打开的文件末尾添加：
				export JAVA_HOME=/usr/lib/java/jdk8
				export JRE_HOME=${JAVA_HOME}/jre
				export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
				export PATH=${JAVA_HOME}/bin:$PATH
			保存退出
			输入命令使之生效：source ~/.bashrc
		4）配置默认JDK
			sudo update-alternatives --install /usr/bin/java java /usr/lib/java/jdk8/bin/java 300
			sudo update-alternatives --install /usr/bin/javac javac /usr/lib/java/jdk8/bin/javac 300
		5）通过命令验证配置是否成功
			java -version
			java
			javac
			
###4、配置Build环境，解压缩工具
		1）sudo apt-get install ant		#build环境
		2）sudo apt-get install unzip
		
###5、配置systemc
		1）将压缩包systemc-2.3.1.gz复制到/home下
		2）解压
			tar -zxvf systemc-2.3.1.gz
		3）编译systemc
			cd systemc-2.3.1	#进入systemc-2.3.1中
			mkdir objdr			#新建文件夹objdr
			cd objdr			#进入文件夹objdr
			../configure CXX=g++ --disable-async-updates		#运行configure
			sudo make install	#编译
			cd ..
			pwd		#记录获得的当前路径为/home/linxiaodan/systemc-2.3.1
			
###6、配置DOL
		1）将压缩包dol_ethz.zip复制到/home下
		2）解压
			mkdir dol		#新建文件夹dol
			unzip dol_ethz.zip -d dol 	#解压到dol中
		3）编译dol
			进入dol中找到build_zip.xml进入（open with gedit），找到下面语句将YYY部分修改为之前记录的路径：
				<property name="systemc.inc" value="YYY/include"/>
				<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
			同时将lib-linux修改为lib-linux64
			cd dol		#进入dol中
			ant -f build_zip.xml all	#编译dol
			之后成功显示build successful
		4）运行第一个例子
			cd build/bin/main
			sudo ant -f runexample.xml -Dnumber=1
			> 出现问题：build failed，提示java的相关问题
			> 解决方法：选择正确的JDK版本
			> 	查看当前各种JDK版本和配置
			> 	sudo update-alternatives --config java
			> 	选择/usr/bin/java下的JDK
			最后重新执行以上语句，成功后显示build successful
			
			
			
			
			
			