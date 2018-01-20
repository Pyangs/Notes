## python logging模块 
##### 在loging模块的应用中，经常使用的组件有loggers、handlers、formatters、filter。
- Logger: 日志类，应用程序往往通过调用它提供的api来记录日志。
- Handler: 对日志信息处理，可以将日志发送(保存)到不同的目标域中。
- Formatter: 日志的格式化。
- Filter：对日志内容或等级的过滤。

## python time
    from datetime import datetime
    now = datetime.now()
    today = datetime.strftime(now,'%Y-%m-%d')

## python 类
##### 类方法
    # here ,cls means the class A() ,not the instance a()
    class A():
        var = 'var'
        def __init__(self):
            pass
            #self.var = 'var'

        def foo(self):
            print self
            self.plus()

        @classmethod
        def plus(cls):
            print cls

    a = A()
    a.foo()
    # <__main__.A instance at 0x7f31dc105ef0>
    # __main__.A

##### 类的方法
    A.foo(a)
    # 等价于
    a.foo()

## python 元类
    # see http://blog.jobbole.com/21351/
    class Foo(object):
        bar = True
    #可以翻译为：
    Foo = type('Foo', (), {'bar':True})
    # 内建函数type即为一种元类，元类就是用来创建类的“东西”，
    # 功能有
    # 1)   拦截类的创建
    # 2)   修改类
    # 3)   返回修改之后的类

