# php学习笔记
## Php的四对标记
- 1、<?php ?>  标准
- 2、<script language=”php”></script>
- 3、<?  ?>   <?=$str ?>  需要在配置文件开启:short_open_tag=On;
- 4、<%  %>   asp风格，也是兼容的，需要修改配置文件：asp_tags=On;
# 为什么不用段标记？
- 从PHP7开始，这种写法<script language="php"></script>，已经不支持了
- 无论在任何时候这种<? ?> <?=?> <%=%>短标签的形式都不推荐使用，兼容性太差了，以后应该也会被废弃，也会和xml代码发生冲突

php文件中为什么有的php有结束符“?> ”，有的没有结束符“?> ”？

如果是PHP和HTML混编时，一定要有结束符号?>，否则有可能导致语法错误。
如果是一个纯粹的PHP页面，最后的结束符?>最好一定不要添加
这样做的好处是：如果这个是一个被别人包含的程序，没有这个结束符，可以减少很多很多问题，比如说：header,
setcookie, session_start这些动作之前不能有输出，如果不小心在?>
后边加了不可见字符（多余的空格、换行符）等破坏页面显示，就会报”Header already
sent”错误，不写的话不会有此问题。

注意：与?>结束的语句可以不加分号，但最好加上。
# 注释：
	单行注释//
	脚本注释#
	多行注释/*   */
	文档注释/**  */
# 变量的声明：
## 1.	变量名以$开始
## 2.	变量的名称要有意义
## 3.	变量名不能以数字开头，不能有运算符，尽量不使用系统关键字
## 4.	变量名称区分大小写（驼峰式命名方式）
#至此提到需要熟悉的一些函数
var_dump ( mixed $expression [, mixed $... ] )	输出变量的相关信息。
bool isset ( mixed $var [, mixed $... ] )	检测变量是否设置，并且不是 NULL。
void unset ( mixed $var [, mixed $... ] )	unset() 销毁指定的变量
bool empty ( mixed $var )	检查一个变量是否为空
变量不存在，null，空字符串
可变变量：
	有时候使用可变变量名是很方便的。就是说，一个变量的变量名可以动态的设置和使用。一个普通的变量通过声明来设置。
注意：在 PHP 的函数和类的方法中，超全局变量不能用作可变变量。$this 变量也是一个特殊变量，不能被动态引用。可变变量$要连在一起、
举例：
		$hello=”hello”
		$$hello=”name”
		$a$hello=”abc”这个是错误的声明
变量的引用
1.	只有变量才有地址，只有变量才能引用
2.	一个变量发生变化，另一个引用变量也会变化
3.	在使用unset()时，如果有引用关系，只是解除了这种引用关系，只是删除一个别名，另一个还在。
4 如果两个变量是引用关系，一个变，另一个也变，但是如果给其中一个引用，不是普通的变量，而是一个引用，则原引用关系解除，建立了新的引用关系
变量的类型：
	PHP支持八种原始类型
		四种标量类型：布尔型（boolean）整型（integer）浮点型（float）(浮点数，也做double) 字符型（string）
		两种复合类型：数组（array）对象（object）
		两种特殊类型：资源（resource）null
		
Boolean
 	Int 0 为假，Floot 0.00和0.0为假值，空字符串、字符串0为假，空字符串为假，空对象为真，特殊类型null为假
整型：
	超过最大值变成float类型
浮点型：
	浮点型是一个近似数，不要用两个浮点数比较是否相等
字符串类型：
	声明一个字符串必须使用单引号或者双引号引起来
	一个字符和多个字符都是字符串
   字符串是没有长度限制
	在单引号中可以使用双引号，在双引号中可以使用单引号
	在单引号中不能再使用单引号，在双引号中不能再使用双引号
	可以使用转义字符\
单引号和双引号的区别
1、在双引号中可以解析变量，但是在单引号中不能解析变量
2、在双引号中可以使用转义字符\n \r \t 在单引号中不能使用转义字符，在单引号中只能转义单引号自己和转义字符
字符串定界符的声明
1.PHP定界符的作用就是按照原样，包括换行格式什么的，输出在其内部的东西； 
2.在PHP定界符中的任何特殊字符都不需要转义； 
3.PHP定界符中的PHP变量会被正常的用其值来替换。 
PHP中的定界符格式是这样的： 

<<<Eof 
…… 
Eof;
定界符注意事项：
1，	使用三个<<<小于号
2，	在开始的定界符（自定义的字符串中）一定要左边挨着<<<，写完定界符的自定义字符串，一定要直接回车（空格都不可以）
3，	在结尾的字符串中，一定要顶头写，和开始的字符串要一致，写完直接回车
4，	使用单引号‘’在开始的定界符中，将支持双引号的功能，改成单引号的功能，例如
$c=<<<'ABC'
这里可以是任合内容
我是历的苛夺基
本原则叶落归根在运
输费艰难田￥￥&……
ABC;
echo $c;
具体三考：https://www.cnblogs.com/zywf/p/4912159.html

改用markdown编辑
