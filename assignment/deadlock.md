###1.	������ͼ
![image](https://github.com/LinXiaodan/ES2016_14353188/raw/master/images/deadlock.PNG)
###2.	����������4����Ҫ����
	���⡢ѭ���ȴ��������ᡢ�����뱣��

###3.	�Գ�����������Ľ���
		����Deadlock����ִ��main���������ȴ���Deadlock����ʱ�ͻ����Deadlock��Ĺ��캯����
	�����µ��߳�t�����߳�t��ӵ����ȶ����У��ȴ�20000��count�ļ���֮�󣬵���a.methodA(b)��
	�����ʱ���õ��ȶ����е��߳�t�����ȣ� �ͻ����run��������run�����е���b.methodB(a)����
	ʱa.methodA(b)��b.methodB(a)ͬʱ����object��һ��synchronized(this)ͬ������飬�ͻᵼ��
	������

