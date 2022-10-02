## C/C++

### C++基础知识

```pdf
pdf/C++语法.pdf
```


### 基本语法

1. [<font face="Monaco">sprintf()</font>函数：将格式化的数据写入字符串_C语言中文网](http://c.biancheng.net/cpp/html/295.html)
   - <font face="Monaco">`sprintf()`</font>的作用是将一个格式化的字符串输出到一个**目的字符串**中，而<font face="Monaco">`printf()`</font>是将一个格式化的字符串**输出到屏幕**。
   - <font face="Monaco">`int sprintf(char *str, char * format [, argument, ...])`</font>。<font face="Monaco">str</font>为要写入的字符串；<font face="Monaco">format</font>为格式化字符串，与<font face="Monaco">`printf()`</font>函数相同；<font face="Monaco">argument</font>为变量。
2. [<font face="Monaco">fscanf()</font>函数：将文件流中的数据格式化输入_C语言中文网](http://c.biancheng.net/cpp/html/2522.html)
2. [C++基础之**uint8_t**_时光机 °的博客-CSDN博客](https://blog.csdn.net/qq_19784349/article/details/82927169)
2. [浅析C语言之uint8_t / uint16_t / uint32_t /uint64_t_海阔天空sky的博客-CSDN博客](https://blog.csdn.net/Mary19920410/article/details/71518130)
2. [求一个数组中出现次数超过n/3的数(C++实现)_zhanyue666的博客-CSDN博客](https://blog.csdn.net/weixin_41106545/article/details/83213354?spm=1001.2101.3001.6650.6&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-6.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-6.pc_relevant_default&utm_relevant_index=8)
2. [开学回归力扣：第十二题—— 229. 求众数 II（摩尔投票法）_xiangguang_fight的博客-CSDN博客](https://blog.csdn.net/xiangguang_fight/article/details/114839642?spm=1001.2101.3001.6650.8&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-8.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~Rate-8.pc_relevant_default&utm_relevant_index=10)
2. 

------



### 毕设遇到的编程问题：

2021年3月24日

- [C语言全局变量多个cpp,c++多个文件中共用一个全局变量 变量跨文件使用_李勖晟的博客-CSDN博客](https://blog.csdn.net/weixin_30684945/article/details/117078693?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_antiscanv2&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_antiscanv2&utm_relevant_index=1)

- [C++将一个cpp文件中的变量应用到另一个cpp文件中_公子恒的博客-CSDN博客](https://blog.csdn.net/qq_27942333/article/details/84719737)

```c
  int i; //声明并定义 
  extern int i; //声明 
  extern int i=10; //定义 
   
  void f(); //声明 
  void f() {}; //定义
```


- [C++ getline函数用法详解 (biancheng.net)](http://c.biancheng.net/view/1345.html)

- [C 库函数 – strcpy() | 菜鸟教程 (runoob.com)](https://www.runoob.com/cprogramming/c-function-strcpy.html)

- [string中c_str()的用法_Lemonbr的博客-CSDN博客_string.c_str](https://blog.csdn.net/qq_41282102/article/details/82695562)

- [C++强制类型转换操作符 static_cast - melonstreet - 博客园 (cnblogs.com)](https://www.cnblogs.com/QG-whz/p/4509710.html)

- [C++类型转换之reinterpret_cast - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/33040213)

- [C++ 报错 error: ‘xxx’ was not declared in this scope_wongHome的博客-CSDN博客](https://blog.csdn.net/qq_39779233/article/details/107585014)

- [const char * 、char const *、 char * const 三者的区别_SilentOB的博客](https://blog.csdn.net/silentob/article/details/76994618)

- [C++中const char*, string 与char*的转化_风居住de街道的博客-CSDN博客](https://blog.csdn.net/zhang_alongzd/article/details/52790905)

- [C++ 中 string和char* 的区别 - Tsingke - 博客园 (cnblogs.com)](https://www.cnblogs.com/tsingke/p/12075078.html)

- [C++ 内存溢出&内存泄漏_AiChiMomo.的博客-CSDN博客_c++ 内存溢出](https://blog.csdn.net/qq_37368095/article/details/88525204?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~CTRLIST~Rate-1.pc_relevant_default&utm_relevant_index=2)

- [从缓冲系统文件到常见栈溢出函数_Retrovich的博客-CSDN博客_函数栈溢出](https://blog.csdn.net/Retrovich/article/details/84623641?spm=1035.2023.3001.6557&utm_medium=distribute.pc_relevant_bbs_down_v2.none-task-blog-2~default~OPENSEARCH~Rate-8.pc_relevant_bbs_down_v2_default&depth_1-utm_source=distribute.pc_relevant_bbs_down_v2.none-task-blog-2~default~OPENSEARCH~Rate-8.pc_relevant_bbs_down_v2_default)

- [文件读写完后fclose（）就内存溢出-CSDN社区](https://bbs.csdn.net/topics/390681492)

- **[C语言自定义函数如何返回数组_renyuxiaomei的博客-CSDN博客_返回数组的函数怎么写](https://blog.csdn.net/renyuxiaomei/article/details/78439864)**

- [用数组作为函数返回值_Gavechan的博客-CSDN博客_数组作为返回值](https://blog.csdn.net/gavechan/article/details/45542913)

- [错误信息was not declared in this scope](https://blog.csdn.net/ac1085589289/article/details/85077580)

-[C++, 想要使用string ,必须要用命名空间 std](https://blog.csdn.net/sergery/article/details/8144731)

----


### C++生成随机数？

- [C++产生随机数_on_june_7th的博客-CSDN博客_c++随机数](https://blog.csdn.net/on_june_7th/article/details/120392619)
- [C++中rand()函数的用法_风暴计划的博客-CSDN博客_c++ rand()](https://blog.csdn.net/cmm0401/article/details/54599083)
- [C++寻找数组最大值和最小值_Jeff_的博客-CSDN博客_c++求数组中的最大值和最小值](https://blog.csdn.net/weixin_40539125/article/details/82721340)

__`rand()`__ 不需要参数，它会返回一个从 __`0`__ 到最大随机数的任意整数，最大随机数的大小通常是固定的一个大整数。__`int num = rand() % 100`__ ;  所以，num的值就是一个 __`0~99`__ 中的一个随机数了。

如果要产生 __`1~100`__ ，则是这样：

```c++
int num = rand() % 100 + 1; 
```

**总结来说**，可以表示为： __`int num = rand() % n +a`__; 其中的 **`a`** 是起始值， **`n-1+a`** 是终止值， __`n`__ 是整数的范围。

**一般性** ：`rand() % (b-a+1)+ a `;   就表示  __`a~b`__ 之间的一个随机整数。

若要产生 __`0-1`__ 之间的小数，则可以先取得 `0-10`的整数，然后均除以 __`10`__ 即可得到“随机到十分位”的 __`10`__ 个随机小数。

通常 **`rand()`** 产生的随机数在每次运行的时候都是与上一次相同的，这样是为了便于程序的调试。

若要产生每次不同的随机数，则可以使用 **`srand( seed )`** 函数进行产生随机化种子，随着seed的不同，就能够产生     不同的随机数。



