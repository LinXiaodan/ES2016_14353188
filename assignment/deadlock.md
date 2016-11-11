###1.	死锁截图
![image](https://github.com/LinXiaodan/ES2016_14353188/raw/master/images/deadlock.PNG)
###2.	产生死锁的4个必要条件
	互斥、循环等待、不剥夺、请求与保持

###3.	对程序产生死锁的解释
		运行Deadlock，会执行main函数，首先创建Deadlock，这时就会调用Deadlock类的构造函数：
	创建新的线程t，将线程t添加到调度队列中，等待20000次count的减法之后，调用a.methodA(b)。
	如果此时正好调度队列中的线程t被调度， 就会调用run函数，在run函数中调用b.methodB(a)，这
	时a.methodA(b)和b.methodB(a)同时访问object的一个synchronized(this)同步代码块，就会导致
	死锁。

