###Chapter 3


	字符串不可变, string[-3:]='com' 这样是不行的
	
	string 模版字符串 

	from string import Template
	s = Template('${x},glorious ${x}!')
	s.substitute(x='slurm')

	输出 $ % \ 需要double  $$ %% \\ //

	字段宽度 和 精度
	
	'％10f' % pi
	'     3.14159'
	
	'%.5s' % 'fujianwei'
	'fujia'	
	
	'％010f' % pi
	'0003.14159' 用0填充
	
	s.find('x')
	s.index('x')
	index和find都会返回字符串开始的索引值，index会抛异常，find会返回-1。

	s.replace('','')
	
	s.strip(' *!') 去除左右2边的字符多个
	
	replace 和 translate
	
	translate可以批量替换
	

###Chapter 4

	item = [('name','jianwei'),('age','23')]
	d  = dict(item)
	d = dict('name'='jianwei','age'='23') 
	
	key:value
	
	字典的格式化字符串
	>>>d = {'name':'jianwei','age':'23'}
	>>>"some balab %(name)s,%(age)s" % d
	"some balab jianwei,23"
	可对应多个
	
	
	－－－
	x={}
	y=x
	x['key']='value'
	x={}
	y不变，还是有值
	
	x = {}
	y = x
	x['key'] = 'value'
	x.clear()
	y值也清除了
	
	dict 中的浅复制、深复制
	浅复制 改变值，没关系，删除值都一样
	以上情况，需要深复制
	
	
	fromkeys:
	{}.fromkeys(['name','age'])
	构造一个空字典 ，每个键默认值为None
	{}.fromkeys(['name','age'],'(unkonwn)') 提供默认值
	
	不存在
	dict.get('name') None 
		dict.get('name','N/A') 提供默认值
		dict.get('name','not available') 提供默认值
	dict['name'] error
	
	* dict.has_key('name') = key in dict   (has_key 不在python3)
	
	* items将所有字典项以列表返回,没有特殊顺序
	d = {'name':'jianwei','age':'23'}
	>>> d.items()
	[('name','jianwei'),('age','23')]
	
	* iteritems 返回迭代器对象
	
	* keys iterkeys 
	
	* pop 将指定键－值对删除
	* popitem 随机删除key-value 返回这个key-value
	
	* setdefault('name','N/A') 类似get ,不存在key时，设置key，默认值为后面 
	
	* update 
	>>>d = {'name':'jianwei','age':'23'}
	
	>>>x = {'name','Fujianwei'}
	>>>d.update(x)
	{'name':'Fujianwei','age':'23'}
	
	
	* values(),itervalues  返回值 还有 迭代器
	
###Chapter 5

	>>> age = -1
	>>> assert 0 < age < 100, 'The age must be realistic'
	Traceback (....)
	  File "<stdin>".line 1 in?
	AssertionError: The age must be realistic
	
	 
	range & xrang (range转换为xrange Python3.0)
	#range可以返回一个可以用于所有目的的普通列表对象，而xrange将返回一个特殊目的的对象，尤其适用于迭代操作，但是xrange并不返回一个迭代器，如果需要这样一个迭代器，可以调用iter(xrange(x))。xrange返回的特殊目的对象比range返回的列表对象消耗较少的内存（范围比较大的时候）。但是对特殊目的对象执行循环操作的开销略微高于对列表执行循环的开销。xrange迭代大的序列比较高效

	>>>print range(5)
	[0, 1, 2, 3, 4]
	>>> print xrange(5)
	xrange(5)
	#其中，range将返回一个普通列表，但是xrange将返回一个特殊目的对象，将显示为其自身的特殊方式。
	
	迭代工具
	
	>>>name = ['jianwei','Mike','Jane']
	>>>age = ['23','32','22']
	>>>zip(name,age)
	[('jianwei','23'),('Mike','32'),('Jane','22')]
	
	enumerate() 提供索引-值
	
	for index,string in enumerate(strings):
		some statements...
		
	列表的   list.sort()
			list.reverse()
	reversed(s)
	sorted(s)
	不修改，返回函数作用的
	
	
	列表推导式
	>>>[(x,y) for x in range(3) for y in range(3)]
	[(1,1),(1,2),(1,3),...(3,1),(3,2),(3,3)]
	
	*exec
	>>> exec "print 'hello,fujianwei'"
	>>> exec "print 'sqrt = 1'" in scope 
	>>scope['sqrt']
	1
	
	*evel 会执行一系列python语句
	>>> evel(raw_input('enter:'))
	enter: 6 + 8 * 2
	22
	

###Chapter 6
	
	>>> def test(x):
		'some doc'
		reuturn x * x
	>>> test.__doc__
	some doc
	
	>>> help(test)
	输出介绍
	
	s = [1,2,3,5]
	w = [:] 复制值
	m = s  指向同一个
	
	所以 
	>>>def test(k)
		some statement
		
	>>>test(s)
	会影响到列表
	
	>>>def test(*params):
		return params
		
	返回元组
	
	>>> def test(**params):
			return params
	>>> test(n=1,m=2,s=3)
	{n:1,m:2,s=3}
	
	>>>map(str,range(5))
	['0','1','2','3','4']
	map函数可以将序列里面的数传统给一个函数，不用带括号
	
	lambda 匿名函数
	
	filter(func,seq) 返回其函数为真的元素的列表
	