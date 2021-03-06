# IDAPythonScripts
----------------------------------------

> IDAPythonScripts: 二进制漏洞静态分析检测脚本(IDA Pro)

![IDA Pro女神](https://images.gitee.com/uploads/images/2021/0202/213402_4cd1b95c_2323666.jpeg)

#### QQ交流群：813115551
#### 加微信-进入交流群：wwy18795980897

## 准备
----------------------------------------

  * 首先下载IDA Pro软件，版本 <= 6.8，7.0以上部分脚本不支持。
  * 安装IDAPython插件。  
    IDAPython7.0链接: https://pan.baidu.com/s/14ooTvM5VViOm9EWZT5WP5g 密码: kg6y
  
  
## 漏洞内容（待更新）
----------------------------------------

 1. 危险函数调用  
      此脚本对IDA反汇编文件进行静态分析，检测其是否调用了可能产生漏洞的危险函数，没有找到汇编中的统一的危险函数集合，只好自己一点点积累，在functions.sql中可以看到一些常见的危险函数，保存在MySQL数据库中以后也方便Python调用。
	  
 2. 栈堆缓冲区溢出漏洞  
      脚本从函数调用的地址向后跟踪推送到堆栈中的参数，并返回与指定参数对应的操作数。然后确定eax在被推入堆栈时是否指向堆栈缓冲区，存在可能造成堆栈缓冲区溢出的利用点。
	  [参考链接](https://www.somersetrecon.com/blog/2018/7/6/introduction-to-idapython-for-vulnerability-hunting)  
	  只能在IDA版本小于6.8上使用，IDA7.0报错。
	   
 3. 格式化字符串漏洞  
      该脚本结合Github上开源IDA插件[LazyIDA](https://github.com/L4ys/LazyIDA/blob/master/)，吸收了其中对格式化字符串漏洞检测方法，使其功能在Python脚本中得以实现。
	  
 4. 整型溢出漏洞  
      脚本首先计算当前分配给函数的内存大小，而后从IDA反汇编文件中找到各个函数的参数大小，并进行比较，检测是否存在“整型”溢出的可能。
	  [参考链接1](https://www.cnblogs.com/M-Mr/p/3925096.html)&nbsp;[参考链接2](https://blog.csdn.net/qq_21063873/article/details/77678619)&nbsp;[参考链接3](https://blog.csdn.net/luckyjoy521/article/details/12905405)  
	  缓冲区是变化的，因此检测出整型溢出的可能性很大，但是想要利用起来相对更难。  
	  脚本执行完毕后会造成IDA闪退，原因未知...  
  ...

  
## 关于更新
----------------------------------------

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;漏洞都已经过测试，第一次首先发布4个已经成功检测的漏洞脚本，有一些地方仍然鸡肋，还需大佬支持改善。IDA是一个强大的反汇编分析软件，其中IDAPython插件可以简化手工分析过程，提高测试效率，然而国内对IDA的教学并不多，IDAPython插件的脚本编写更是如此，希望通过这个小仓库丰富IDAPython针对各类漏洞的分析脚本，前人栽树，后人乘凉。真心希望能够与大佬们多多交流学习，带带小白，微信：wwy18795980897。


## 感谢
----------------------------------------

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;部分脚本是在国内外众多大佬编写的模块上进行的代码加工，功能整合，是他们的默默奉献让这里的脚本壮大起来，以及发布在Github，Twitter，CSDN，安全客，FreeBuf等平台上的精彩文章，总是能让我眼前一亮，给我更多的灵感，感谢你们！！！

#### 项目连接
Gitee：https://gitee.com/wwy2018/IDAPythonScripts
