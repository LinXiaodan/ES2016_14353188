DOL配置
======================================

###1、电脑中已经安装好了VMware，在VWware中安装Ubuntu16.0

###2、sudo apt-get update #更新原信息
		出现问题：E:Could not lock /var/lib/dpkg/lock -open
		可能原因：可能上次安装没正常完成，导致资源被锁
		解决方式：将var/lib/apt/liists中的文件全部删掉
					sudo rm /var/cache/apt/archives/lock
					sudo rm /var/lib/dpkg/lock
		之后重新开始又出现问题：Err:1 urlA
								Err:2 urlB
								Err:3 urlC
									Temporary failure resolving 'us.archiv.ubuntu.com'
								......
		原因：无法连接网站
		解决方式：修改DNS
					sudo nano /etc/resolv.conf
					将已有DNS记录使用“#”注释掉，再添加新的DNS记录，如下
						nameserver 8.8.8.8
						nameserver 8.8.4.4
					使用“ctrl+x”保存文件
					锁定文件防止修改DNS
						sudo chattr +i /etc/resolv.conf
					
###3、
	