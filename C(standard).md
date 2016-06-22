#C standard
###基本原则
    K&R编码风格（偏BSD子类）。
    每行不能超过80列。
    默认对齐单元是4个空格。
    除宏定义外，字母均为小写，单词间用下划线_间隔。
    使用C方式的注释，不得使用//形式注释。
    中缀运算符的前后须空一格，如3 + 2以及a > 3。
    逗号后须空一格，如foo(a, b, c);

###宏
	宏声明统一使用英文单词的大写， 单词之间用_分割， 多行声明语句的宏使用do{}while(0)包裹， 比如
    #define macrofun(a, b, c) 			\
		do {					\
			if (a == 5)			\
				do_this(b, c);		\
		} while (0)

###文件
	头文件统一使用如下代码包裹
    #ifndef XXX_H
    #define XXX_H
    #endif /* XXX_H */
    函数声明，变量声明， 结构体， 联合体，宏包含在头文件中， 头文件中不应该包含
    任何的定义， 包含系统头文件使用#include <xxx.h>，包含自己定义的头文件使用
    #include "xxx.h" ，缩进暂用4个字符宽度。
    
###函数
	普通函数名使用英文单词缩写组成，单词之间使用下划线隔开， 内联函数统一在函数
    函数名后面加_inline，标识此函数是内联函数。static函数前后都加双下划线，如
    static __functionName__, 标识为函数此文件私有，函数声明统一在对应头文件。

* 函数声明
```c
return-type function-name (parameter-list);
```

* 函数定义
```c
return-type
function-name (parameter-list)
{
    function-body
}
```

* 函数调用
```c
function-name (parameters)
```

###声明
	关键字后面需要有一个空格，左大括号跟随，右大括号单独占用一行，else的两个大括
    号在同一行, 当条件下面只有一个表达式语句时不加大括号，比如
    if (a > 1)
    	return true;
    else
    	return false;
    如果超过一个表达式语句时加大括号，比如
    if (a > 1) {
    	a += 1;
        return true;
    } else {
    	a -= 1;
        return false;
    }
    但是do{}while()是个特例，右大括号不单独占用一行，比如
    do {
        do something
    } while (0)

* for 声明
```c
for (initialize; test; step) {
	statement
}
```

* switch 声明
```c
switch (a) {
	case 'A':
    	break;
    case 'B':
    	break;
    default:
    	break;
}
```

* 函数内部变量声明
变量的声明做到上下对其，长度由小到到，缩减以最后声明空2个字符为准， 相同用途变量
声明在同一行,比如
```c
return-type
function-name (parameter-list)
{
	int             i;
    int             j;
    char            *name;
    struct student  stu;
    
    expresss;
}
```

* 结构体, 枚举类型和联合体声明
结构体名字都使用小写字母，使用typedef声明结构体别名的时候，统一结尾加_t, 声明结
构体别名指针的时候，统一结尾加_ptr,比如
```c
 typedef struct fish
 {
	float  weight;
	float  length;
	float  probability_of_being_caught;
 } fish_t, *fish_ptr;
```
枚举类型每一个值单独占一行
```c
enum enum_num {
    ONE,
    TWO,
    THREE
};

###表达式
	表达式每个token之间需要用空格分开，避免符号优先级引起的歧义，统一加小括号，
    比如 a = ((b + 1) * 2) >> 2

###参考标准
* [nginx code style](http://tengine.taobao.org/book/appendix_a.html)
* [linux kernel code style](http://www.linuxfromscratch.org/alfs/view/hacker/part2/hacker/coding-style.html)

###代码编译标准
gcc5 -std=gnu11  [GNU C](https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html)
