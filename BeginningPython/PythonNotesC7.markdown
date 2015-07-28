###Chapter 7

	* 多态
	* 封装
	* 继承
	
	repr(x) 原来的
	
	特征在外部可以访问,self就是对象本身,普通函数就不用self，方法有
	class Person:
		def setName(self,name):
			self.name = name 
		def getName(self):
			return self.name		
	>>>foo = Person()
	>>>foo.setName('NIhao')
	>>>foo.getName()
	NIhao
	>>>foo.name = 'Jianwei'
	>>>foo.getName()
	Jianwei
	>>>Person.greet(foo)
	Jianwei
	
	* 方法或者特性私有 __ 名字前面加(双下划线),
	
	class test:
		def setName(self,name):
			self.name = name
		def greet(self):
			print 'hello,%s' % self.name
			__invisiable()
		def __invisiable(self):
			print 'This is invisiable'
	
	>>> w = test()
	>>> w.setName('Jianwei')
	>>> w.__invisiable()
	error....balabala
	>>> w.greet()
	hello,jianwei
	This is invisiable
	
	class baseClass:
		def init(self):
			pass
	class ExtendClass(baseClass):
		def init(self):
			pass
	
	超类（基类）baseClase
	
	子类			ExtendClass
	>>issubclass(ExtendClass,baseClass)
	True
	
	isinstance 检查一个对象是否是一个类的实例
	
	多重继承
	
	class className(baseClass1,baseClass2):
		pass
	先继承的类的方法会重写后继承类的方法，比如 baseClass1有talk(),会重写baseClass2的talk()方法
	

###Chapter 8

	class MutilCalculator():
	  value = True
	  def calc(self,expression):
		try:
			return eval(expression)
		except ZeroDivisionError:
			if self.value :
				print 'ZeroDivisionError....'
			else:
				raise	# 异常
		except TypeError:
			print 'TypeError...'		
	
	人为可以控制value的值
	
	或者可以捕捉多个异常 ,捕捉对象
		except (ZeroDivisionError,TypeError,NameError), e:
			print e
			
	test = MutilCalculator()
	test.value = True
	test.calc('1+2')
	
	
	try:
		....
	except:
		....
	else:
		....
		
	如果try ok ，执行 else
	否则就在except的内容
	
	try:
		...
	except:
		...
	finally:
		...
	or try: except: else: finally
	finally肯定会执行
	
###Chapter 9
				
	super()
	property()
	
	staticmethod() 静态方法  没有self参数 且能被类本身直接调用
	classmethod()	类成员方法
	
	@ 装饰器  在方法或函数的上方将装饰器列出，从而指定一个或者多个的装饰器（多个装饰器在应用时的顺序与制定顺序相反）
	
	
	迭代器 __iter__
	
`yield 生成器` ***important
	
	[wolfram MathWorld](http://mathworld.wolfram.com/Graph.html)
	
	与 return 区别 return 返回值，yield每次产生多个值
	
	生成器推导式 可以迭代
	>>> g = (x for x in range(2,12))
	>>> g.next()
	
###Chapter 10

	sys
	os
	fileinput
	set
	heapq
	deque
	time
	random
	shelve
		潜在的陷阱：写入需要副本来保存 shelve.open函数返回的对象并不是普通的某某类型（如字典映射）p206-207
		或者添加 writeback=true参数
	
	re模块
	compile
	search
	match
	split
	findall
	sub
	escape
	
###Chapter 11
	
	'r' 读模式
	'w' 写模式
	'a' 追加模式
	'b' 二进制 声音图像等..'rb'读取二进制
	'+' 读/写
	UNIX 换行 \n
	Windows 换行 \r\n
	
###Chapter 12

	一些支持GUI的Python工具包
	
	Tkinter
	wxpython
	PythonWin
	Java Swing
	PyGTK
	PyQt
	
###Chapter 13

	close() 关闭连接之后，连接对象和它的游标均不可用
	commit() 如果支持的话就提交挂起的事务，否则不做任何事
	rollback() 回滚挂起的事务(可能不可用)
	cursor() 返回链接的游标对象
	
###Chapter 14

	服务器套接字 （需要监听 处理多个链接 较复杂）
	客户端套接字	（简单链接 完成事务 断开连接）
	
	socket 3个参数 
		* 地址族(socket.AF_INET)
		* 流(socket.SOCK_STREAM)或数据报(socket.SOCK_DGRAM)
		* 使用协议(默认 0 使用默认值就可以)
	
	服务器端用bind方法后，再调用listen去监听这个给定的地址
	客户端套接字使用connect方法连接到服务器在connect方法中使用的地址与bind方法中的地址相同
	服务器端套接字开始坚挺后，它就可以接受客户端的连接，这个步骤使用accept方法完成，这个方法会阻塞(等待)直到客户端连接，然后该方法就返回一个格式为(client,address)的元组，client是一个客户端套接字，address是地址。。＃这种称为阻塞或同步网络编程 ＃
	

