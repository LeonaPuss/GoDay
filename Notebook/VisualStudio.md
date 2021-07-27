#visual studio语音切换

 在“工具tools”菜单中单击“选项options”------>环境Environment---------->区域设置International Settings ------------>选择语言。我的这儿默认为“与windows系统相同”


#Visual Studio 项目中添加include, lib, dll库文件（*.h,*.lib,*.dll）

应用程序使用外部库时需要进行加载，两种库的加载本质上都是一样：提供功能和功能的定义。vs2005 c++ 项目设置外部库方法如下：

1. 添加编译所需要（依赖）的 lib 文件
     在“项目->属性->配置属性->连接器->输入->附加依赖项”里填写“winsock.lib”，多个 lib 以空格隔开。等同于“#pragma comment(lib, "*.lib") ”语句。


2. 添加库（libs）文件目录
     方法 1：项目->属性->配置属性->连接器->常规->附加库目录”
     方法 2：[菜单]“工具->选项->项目和解决方案->c++ 目录”，选择对应平台，然后添加所需“库文件”目录
     这个设置类似于设置环境变量，主要是为程序设置搜索的库目录，真正进行库加载还需要进行第一种设置！


3. 添加包含（include）文件目录
     方法 1：“项目->属性->配置属性->c/c++->常规->附加包含目录”
     方法 2：[菜单]“工具->选项->项目和解决方案->c++ 目录”，添加所需“包括文件”目录
     方法2类似于设置环境变量。
4. 导入库（import）
    在“项目->属性->配置属性->连接器->高级->导入库”填写需要生成的导入库

 

相对路径的设置
     在VS的工程中常常要设置头文件的包含路径，当然你可以使用绝对路径，但是如果你这样设置了你只能在你自己的机器上运行该工程；如果其他人拷贝你的工程到其他机器上就可能无法运行，这个是因为你在建工程时可能把工程放在了E:盘，但是其他人可能会把工程放在其他根目录下，这样会导致找不到头文件问题。
对于新手，在设置绝对路径时往往会犯浑，他们不清楚这里的“相对”究竟是以什么位置为起点。其实这里的相对路径就是相当于工程文件（XXXX.vcproj）为起点零计算出的能找到包含所需头文件（也就是找包含所需头文件的include目录）的路径。
例如你的工程文件（Count.vcproj）所在目录路径为：
E:\projects\Count\Count\Count.vcproj
该工程需要包含一个图片参数，该图片所在路径如下：
E:\projects\Count\pic\pic01.jpg
这里程序中的相对路径设置如下：
..\\pic\\pic02.jpg



程序代码中的参数路径设置时要用双斜线：
例如：
#include "..\TestLib\lib.h"
#pragma comment(lib,"..\\debug\\TestLib.lib");

Visual Studio Code 如何编写运行 C、C++ 程序？
https://www.zhihu.com/question/30315894
 张玉生《C语言程序设计实训教程》双色版 配套实验书答案
https://blog.csdn.net/weixin_45303797/category_10870394.html

C语言程序设计双色版(张玉生) 课后习题参考答案
https://www.jb51.net/books/770612.html

C++面经200问：逆袭进大厂
https://www.jb51.net/books/774960.html

Google C++编程风格指南
https://www.jb51.net/books/726143.html

C语言实验指导书2021版 中文PDF版
https://www.jb51.net/books/779996.html

C++ Primer Plus中文版(第6版) 
https://www.jb51.net/books/193957.html

C++并发编程实战第二版 (C++ Concurrency in Action) 中文
https://www.jb51.net/books/779206.html

嵌入式C语言自我修养
https://www.jb51.net/books/776579.html

Visual Studio 2019编写C语言的使用方法
https://blog.csdn.net/lj317499/article/details/109401024

https://blog.csdn.net/qq_34573534/article/details/108556227


VS Sample 