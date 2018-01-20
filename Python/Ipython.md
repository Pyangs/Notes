## 魔术命令
##### 命令  说明
    %quickref     # 显示IPython的快速参考
    %magic     # 显示所有魔术命令的详细文档
    %debug     # 从最新的异常跟踪的底部进入交互式调试器
    %hist     # 打印命令的输入（可选输出）历史
    %pdb     # 在异常发生后自动进入调试器
    %paste     # 执行剪贴板中的Python代码
    %cpaste     # 打开一个特殊提示符以便手工粘贴待执行的Python代码
    %reset     # 删除interactive命名空间中的全部变量/名称
    %page OBJECT     # 通过分页器打印输出OBJECT
    %run script.py     # 在IPython中执行一个Python脚本文件
    %prun statement     # 通过cProfile执行statement，并打印分析器的输出结果
    %time statement     # 报告statement的执行时间
    %timeit statement     # 多次执行statement以计算系综平均执行时间。对那些执行时间非常小的代码很有用
    %who、%who_ls、%whos     # 显示interactive命名空间中定义的变量，信息级别/冗余度可变
    %xdel variable     # 删除variable，并尝试清除其在IPython中的对象上的一切引用
    %reload_ext         #重新载入该文件

## 奇技淫巧
##### 重写 reload
    def myrl():
        %reload_ext main
        print 'reloaded '

##### 测试函数用时
    timeit foo()


