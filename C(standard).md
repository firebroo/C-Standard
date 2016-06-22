#C standard
###文件
	头文件统一使用如下代码包裹
    #ifndef XXX_H
    #define XXX_H
    #endif /* XXX_H */
    函数声明，变量声明， 结构体， 联合体，宏包含在头文件中， 头文件中不应该包含任何的定义， 包含系统头文件使用#include <xxx.h>，包含自己定义的头文件使用#include "xxx.h", 。
    
###函数
	普通函数名使用英文单词缩写组成，单词之间使用下划线隔开， 内联函数统一在函数函数名后面加_inline，标识此函数是内联函数。static函数前后都加双下划线，如static __functionName__, 标识为函数此文件私有，函数声明统一在对应头文件。

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
	关键字后面需要有一个空格，大括号都单独暂用一行， 当条件下面只有一个表达式语句时不加大括号，比如
    if (a > 1)
    	return true;
    else
    	return false;
    如果超过一个表达式语句时加大括号，比如
    if (a > 1)
    {
    	a += 1;
        return true;
    }
    else 
    {
    	a -= 1;
        return false;
    }

* for声明
```c
for (initialize; test; step)
{
		statement
}
```

* 函数内部变量声明
变量的声明做到上下对其， 相同用途变量声明在同一行
```c
return-type
function-name (parameter-list)
{
	int	i;
    int	j;
    
    expresss;
}
```

* 结构体和联合体声明
使用typedef声明结构体别名的时候，统一结尾加_t, 声明结构体别名指针的时候，统一结尾加_ptr
```c
 typedef struct fish
 {
       float weight;
       float length;
       float probability_of_being_caught;
 } fish_t, *fish_ptr;
```

###表达式
	表达式每个token之间需要用空格分开，避免符号优先级引起的歧义，统一加小括号，比如
    a = ((b + 1) * 2) >> 2
