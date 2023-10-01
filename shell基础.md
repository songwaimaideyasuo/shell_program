# 一、什么是shell
shell英文为贝壳，shell的作⽤是：
解释执⾏⽤户输⼊的命令或程序等。
⽤户输⼊⼀条命令，shell就解释⼀条。
键盘输⼊命令，Linux给与响应的⽅式，称之为交互式。

shell是⼀块包裹着系统核⼼的壳，处于操作系统的最外层，与⽤户直接对话，把⽤户的输⼊， 解释 给操作系统，
然后处理操作系统的输出结果，输出到屏幕给与⽤户看到结果。
关系可以看出这样：
![在这里插入图片描述](https://img-blog.csdnimg.cn/0b279f8f13cc41029e7a5d8c6f406795.png)

我们进⼊到Linux交互式界⾯，所有的操作，都是交给shell解释并执⾏
![在这里插入图片描述](https://img-blog.csdnimg.cn/409af4deaaf34b63a65b00d9885d315d.png)

## 为什么要学习和使用shell？
我们想要获取计算机的数据，不可能每次都编写程序，编译后，再运⾏，再得到我们想要的，例如你想找到⼀个⽂件，可以先写⼀段C语⾔的代码，然后调⽤系统函数，通过gcc编译后，运⾏程序才能找到⽂件。

因此有⼤⽜开发出了shell解释器，能够让我们⽅便的使⽤Linux，例如只要敲下 ls -lh 这样的字符串，shell解释
器就会针对这句话翻译，解释成 ls -l -h 然后执⾏，通过终端输出结果，⽆论是图形化或是命令⾏界⾯。
即使我们⽤的图形化，点点点的动作，区别也只是
命令⾏操作，shell解释执⾏后，输出结果到⿊屏命令⾏界⾯
图形化操作，shell接受点击动作，输出图案数据

## 什么是shell脚本 
当命令或者程序语句写在⽂件中，我们执⾏⽂件，读取其中的代码，这个程序⽂件就称之为shell脚本。
在shell脚本⾥定义多条Linux命令以及循环控制语句，然后将这些Linux命令⼀次性执⾏完毕，执⾏脚本⽂件的⽅式
称之为，⾮交互式⽅式。

 1. windows中存在 *.bat 批处理脚本
 2. Linux中常⽤ *.sh 脚本⽂件


shell脚本规则
在Linux系统中，shell脚本或者称之为（bash shell程序）通常都是vim编辑，由Linux命令、bash shell指令、逻辑
控制语句和注释信息组成。
Shebang 

计算机程序中， shebang 指的是出现在⽂本⽂件的第⼀⾏前两个字符 #!
![在这里插入图片描述](https://img-blog.csdnimg.cn/7e6cc4fa58ee4e69ac58b663822ce150.png)
在Unix系统中，程序会分析 shebang 后⾯的内容，作为解释器的指令，例如:
 1. 以 #!/bin/sh 开头的⽂件，程序在执⾏的时候会调⽤ /bin/sh ，也就是bash解释器
 2. 以 #!/usr/bin/python 开头的⽂件，代表指定python解释器去执⾏
 3. 以 #!/usr/bin/env 解释器名称 ，是⼀种在不同平台上都能正确找到解释器的办法

注意事项：
 - 如果脚本未指定 shebang ，脚本执⾏的时候，默认⽤当前shell去解释脚本，即 $SHELL
 - 如果 shebang 指定了可执⾏的解释器，如 /bin/bash /usr/bin/python
   ，脚本在执⾏时，⽂件名会作为参数传递给解释器
 - 如果#!指定的解释程序没有可执⾏权限，则会报错“bad interpreter: Permission denied”。
 - 如果#!指定的解释程序不是⼀个可执⾏⽂件，那么指定的解释程序会被忽略，转⽽交给当前的SHELL去执⾏这个脚本。
 - 如果#!指定的解释程序不存在，那么会报错“bad interpreter: No such file or directory”。
 - #!之后的解释程序，需要写其绝对路径（如：#!/bin/bash），它是不会⾃动到$PATH中寻找解释器的。
 - 如果你使⽤"bash test.sh"这样的命令来执⾏脚本，那么#!这⼀⾏将会被忽略掉，解释器当然是⽤命令⾏中显 式指定的bash。

# 二、执行shell脚本
## 怎么执行shell脚本
执行shll脚本的方法很简单，直接用./+脚本文件就可以执行。

但会出现一些问题：
我们直接用./去执行时会出现权限不足
可以用两方法解决：
1.直接指定用Linux下的/bin/bash来执行脚本
![在这里插入图片描述](https://img-blog.csdnimg.cn/a312a5db21f341a8bf6a55a8bf7d58d6.png)
2.用chmod +x 来增加执行的权限
![在这里插入图片描述](https://img-blog.csdnimg.cn/6c7da74cede2470ba5644e7f99c54944.png)

我们再创建一个hello.py
![在这里插入图片描述](https://img-blog.csdnimg.cn/9958cde8e81746e5a8fd960f15c248d3.png)用./hello.py来执行它
![在这里插入图片描述](https://img-blog.csdnimg.cn/1c0e995fbc9e4fae9a54c56c31405185.png)
出现了错误，因为脚本未指定 shebang ，脚本执⾏的时候，默认⽤当前shell去解释脚本，即 $SHELL（/bin/bash）

所以我们要指定用python解释器去执行它
#!/usr/bin/python
![在这里插入图片描述](https://img-blog.csdnimg.cn/939668620e9a4605a60909417f81c246.png)
再来执行它
![在这里插入图片描述](https://img-blog.csdnimg.cn/2a41404028604a2db34cae9395001878.png)
又出现错误了，这是因为python对编码的识别错误
我们还要加上# coding:utf-8
之后我们再执行，成功了
![在这里插入图片描述](https://img-blog.csdnimg.cn/9626e0c783cd49128dbf4fe904ad49c9.png)

## 脚本注释，脚本开发规范 

 - 在shell脚本中，#后⾯的内容代表注释掉的内容，提供给开发者或使⽤者观看，系统会忽略此⾏
 - 注释可以单独写⼀⾏，也可以跟在命令后⾯
 - 尽量保持爱写注释的习惯，便于以后回顾代码的含义，尽量使⽤英⽂、⽽⾮中⽂
```powershell
#! /bin/bash
# Date : 2019-11-28 14:59:18
# Author：created by chaoge
# Blog：www.cnblogs.com/pyyu
```

# 三、shell和运维
shell脚本语⾔很适合处理纯⽂本类型数据，且Linux的哲学思想就是⼀切皆⽂件，如⽇志、配置⽂件、⽂本、⽹⻚
⽂件，⼤多数都是纯⽂本类型的，因此shell可以⽅便的进⾏⽂本处理，好⽐强⼤的Linux三剑客（grep、sed、awk）


# 四、脚本语言
## shell脚本语言

shell脚本语⾔属于⼀种弱类型语⾔ ⽆需声明变量类型，直接定义使⽤。

而强类型语⾔，必须先定义变量类型，确定是数字、字符串等，之后再赋予同类型的值。

centos7系统中⽀持的shell情况，有如下种类：
![在这里插入图片描述](https://img-blog.csdnimg.cn/3b8fcd6711674f3c8237d1489bd2d8c1.png)
默认的sh解释器
![在这里插入图片描述](https://img-blog.csdnimg.cn/eca8aab12bf3495aa343483577b8bd5d.png)

## 其他脚本语言

 - PHP是⽹⻚程序语⾔，专注于Web⻚⾯开发，诸多开源产品，wordpress、discuz开源产品都是PHP开发
 - Perl语⾔，擅⻓⽀持强⼤的正则表达式，以及运维⼯具的开发
 - Python语⾔，明星语⾔，不仅适⽤于脚本程序开发，也擅⻓Web⻚⾯开发，如（系统后台，资产管理平
   台），爬⾍程序开发，⼤量Linux运维⼯具也由python开发，甚⾄于游戏开发也使⽤

## shell的优势 
虽然有诸多脚本编程语⾔，但是对于Linux操作系统内部应⽤⽽⾔，shell是最好的⼯具，Linux底层命令都⽀持shell语句，以及结合三剑客(grep、sed、awk)进⾏⾼级⽤法。
擅⻓系统管理脚本开发，如软件启停脚本、监控报警脚本、⽇志分析脚本
每个语⾔都有⾃⼰擅⻓的地⽅，扬⻓避短，达到⾼效运维的⽬的是最合适的。