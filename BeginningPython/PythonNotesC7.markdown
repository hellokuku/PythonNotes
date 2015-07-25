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