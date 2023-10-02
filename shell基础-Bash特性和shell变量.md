> @[TOC](文章目录)
>
> ---
>
> # 一、Bash特性
> ## bash基础特性
> ● bash是一 个命令处理器，运行在文本窗口中，并能执行用户直接输入的命令
> ● bash还能从文件中读取linxu命令，称之为脚本
> ● bash支持通配符、 管道、命令替换、条件判断等逻辑控制语句
> ## 关于历史记录的简单用法
> bash有诸多⽅便的功能，有助于运维⼈员提升⼯作效率
>
> history #命令，查看历史命令记录，注意【包含⽂件中和内存中的历史记录】
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/1fc5716443a144acbe9ce65442b5bdfb.png)
> 最多能看到1000行
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/783e71eb0b34477c9c1ab34ba0e69933.png)
>
> ~/.bash_history里存放用户执行的历史命令
> 我们可以vim ~/.bash_history查看一下
>
> echo $HISTFILE可以看到文件的地址
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/acde8f38a9fa4c98b58fee72a26b263a.png)
>
> history #命令 以及参数
> -c: 清空内存中命令历史；
> -r：从⽂件中恢复历史命令
> 数字 ：显示最近n条命令 history 10
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/94579b1aa05643b785c8e96de0447235.png)
> 这时候我们history，发现历史被清空了
>
> 但是~/.bash_history里的历史还是存在的，所以我们可以用
> history -r ~/.bash_history
> 进行恢复
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/f2b858cb3ed34c7eaa1f6b89049d0a18.png)
>
> 调用历史记录命令
> !历史id，快速执行历史命令
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/b0f8641ba1824ed7b54fac031304ca77.png)
>
> !!可以用来执行上次的命令，或者用上方向键来执行上次命令
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/9443fba5c8b241778caef54f2fc441ff.png)
>
> ## bash特性汇总 
>  - ⽂件路径tab键补全
>  - 命令补全
>  - 快捷键ctrl + a,e,u,k,l
>  - 通配符
>  - 命令历史
>  - 命令别名
>  - 命令⾏展开
>
>
> # 二、shell变量
> ## 变量含义
> 变量是暂时存储数据的地⽅，是⼀种数据标记（房间号，标记了客⼈所在的位置），数据存储在内容空间，通过调⽤正确的变量名字，即可取出对应的值。
> ## shell变量名规则
> 名称定义要做到⻅名知意，切按照规则来，切不得引⽤保留关键字(help检查保留字)
>
>  - 只能包含数字、字⺟、下划线
>  - 不能以数字开头
>  - 不能⽤标点符号
>  - 变量名严格区分⼤⼩写
>  - 
> 例：
> 有效的变量名：
> NAME_CHAOGE
> _chaoge
> chaoge1
> chaogE1
> Chao2_ge
> ⽆效的变量名：
> ?chaoge
> chao*ge
> chao+ge
>
> ## 定义shell变量 
> 单引号变量，不能识别特殊语法
> 双引号变量，能识别特殊符号
>
> 变量定义与赋值，注意变量与值之间不得有空格
> ```powershell
> name="wang"
> 变量名
> 变量类型，bash默认把所有变量都认为是字符串
> 
> bash变量是弱类型，⽆需事先声明类型，是将声明和赋值同时进⾏
> ```
> ## 变量替换/引⽤
> ```powershell
> echo $name #可以省略花括号
> ```
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/dcd74bdbdcf04ee094f82ce2f9789106.png)
> ## 变量的作⽤域
> 本地变量，只针对当前的shell进程
>
> ```powershell
> pstree  #检查进程树
> ```
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/ed86fb1c8ba747b2bf2f75ebcfb36116.png)
>
>  - 环境变量，也称为全局变量，针对当前shell以及其任意⼦进程，环境变量也分⾃定义 、内置两种环境变量
>  - 局部变量，针对在 shell函数 或是 shell脚本 中定义
>
> ⾃定义变量
> ```powershell
> 变量赋值： varName=value
> 变量引⽤： ${varName} 、 $varName
> 单引号，识别为普通字符串
> ```
> ![在这里插入图片描述](https://img-blog.csdnimg.cn/2f212e83764d47238c6eddf12be2fa8a.png)
