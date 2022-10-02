### 看c3程序员C++视频的一些笔记



- [你必须知道的指针基础-8.栈空间与堆空间 - EdisonZhou - 博客园 (cnblogs.com)](https://www.cnblogs.com/edisonchou/p/4669098.html)
- [C++中::和:， .和->的作用和区别? - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/165992745)
- [static与const - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/141437664)
- [一文带你了解static 和const - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/141113043)
- [(2条消息) c++中 new的使用方法_计量小菜鸡的博客-CSDN博客_c++中new的用法](https://blog.csdn.net/qq_15345177/article/details/88066050)
- [C语言中a++与++a的区别 - 简书 (jianshu.com)](https://www.jianshu.com/p/14ac114b9558)
- [c++入门学习篇（1）之：：作用域符解析 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/137383328)
- 

在 C语言 的 switch（开关语句）中，break 语句还可用来在执行完一个 case（分支）后立即跳出当前 switch 结构。



### 输入输出流

cout是个对象，既不是关键字，也不是函数。

1. 可以连续输出
2. 自动识别类型

cin同理

C中不能定义2个相同的变量和函数，会出现重定义

```C++
//cin cout
#include <iostream>
using namespace std;
int main()
{
    int a = 12;
    char b = 'v';
    float c = 34.56;
    cin >> a >> b >> c;
    cout << a <<' ' << b <<' ' << c << endl;
    return 0;
}
```

### 命名空间

```c++
#include <iostream>
using namespace std; //使用命名空间
//命名空间，解决C语言中重定义
namespace stu //声明命名空间
{
    void sort()
    {
        cout << 23 << endl;
    }
}

namespace stu1
{
    void sort()
    {
        cout << 56 <<endl;
    }
}

using namespace stu;
using namespace stu1;
int main()
{
    stu::sort();//::作用域运算符
    stu1::sort();
    return 0;

}
```

![image-20211001101337224](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211001101337224.png)

### 结构体

C语言中结构体看[【C++教程】_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1rW411R7g4?p=10)

1. C++中结构体中可以放函数
2. 声明结构体变量不用struct关键字

```c++
#include <iostream>
using namespace std; //使用命名空间
//命名空间

struct first
{
    int a;
    void fun() //c++结构体中可以放函数
    {
        cout << "Hello wolrd";
    }
    /* data */
};


int main()
{
    first stu; //声明结构体变量不用struct关键字
    stu.a = 23;
    cout << stu.a << endl;
    stu.fun();
    return 0;

}
```



### new & delete

```C++
#include <iostream>
using namespace std;

//heap堆区空间的申请与释放，申请一定要释放
int main()
{
    int *p = new int;  //new + 类型
    float *p1 = new float(134.56); //声明并初始化

    *p = 23; //write
    cout << *p << endl << *p1;  //read

    delete p;  //释放: delete + 指针
    delete p1;
    return 0;

}
------------------------------------------------------------------------
#include <iostream>
using namespace std;

int * test01()
{
	//new的返回值类型是该数据类型的指针
	int *p = new int(10);//开辟一个变量，用10来初始化
	return p;
}

void test02()
{
	//开辟一块数组
	int *arr = new int[10];//arr为该数组的首地址

	for (int i = 0; i < 10; i++)
	{
		arr[i] = i + 10;
	}

	for (int i = 0; i < 10; i++)
	{
		cout << arr[i] << endl;
	}
	delete[]arr;//释放开辟的数组空间
}


int main()
{
	int *p1 = test01();
	cout << *test01() << ' ' << *p1 << endl;
	test02();

	system("pause");
	return 0;
}
```



```C++
#include <iostream>
#include <string.h>
using namespace std;

//heap堆区空间的申请与释放，申请一定要释放
int main()
{//申请数组空间

   int *p  = new int[5];
   //int *p1 = malloc(5*sizeof(int));
   memset(p,0,5*sizeof(int));//初始化
   p[0] = 1;
   p[2] = 3;

   cout<< p[0] << endl << p[2] << endl<< p[4];
   delete[] p;

}
```



### 引用

- 引用声明时必须初始化
- 一个变量可以有多个引用

引用给变量起别名，typedef给类型起别名

```C++
#include <iostream>
#include <string.h>
using namespace std;

int main()
{
   int a = 12;
   int &c = a; //&不是取地址，是引用。声明变量a的一个引用c，c是变量a的别名

   c = 14;
   cout << a << endl;
   return 0;
}
```





![image-20211002165551868](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211002165551868.png)

```C++
#include <iostream>
#include <string.h>
using namespace std;

int main()
{
   //常量类型的引用
   const int &a = 12;
   const char &b = 'v';
   cout << a << endl << b << endl;
//数组的引用
   int arr[10];
   int (&p)[10] = arr; //p的用法和arr一样
   p[0] = 100;
   cout << arr[0] << endl;

   int arr2[2][3];
   int (&p2)[2][3] = arr2;
   p2[2][3] = 67;
   cout << arr2[2][3]<<endl;
   //指针的引用
// 类型 + 引用
   int c = 78;
   int *point = &c;
   cout << *point<<endl;
   int* (&p3) = point;
   *p3 = 97;
   cout << c;
   return 0;
}
```

### 引用做参数

传递参数的过程也是初始化的过程

```C++
#include <iostream>
#include <string.h>
using namespace std;

//引用做参数
void fun(int &a)
{
   a = 19;//操作的是同一块空间
   //cout << a<<endl;
}
//整型做参数
void fun1(int a)
{
   cout << a<<endl;
}
//指针做参数，修改函数外部的值
void fun2(int *a)
{
   *a = 46;
}
int main()
{
   int b = 14;
   fun(b);
   cout << b<<endl;// 通过外部一个函数修改b的值，修改函数外部的值。

   fun2(&b);
   cout<<b;
   return 0;
}
```



### for循环

```c++
#include <iostream>
#include <string.h>
using namespace std;

//增强型for循环
int main()
{
	for(int i = 0; i < 5; i++)
	{
		cout<<i <<endl;
	}
	return
```

### 函数缺省值

```c++
#include <iostream>
using namespace std;
//函数默认值

void fun3(int a = 45, float g = 67.98);

void fun(int a = 12, char b = 'm') //全部指定
{
	cout << a <<' ' << b << endl;
}

void fun2(int a , char b ,float f = 123.78)//部分指定，从右到左，连续指定
{
	cout << a <<' ' << b <<' ' << f <<endl;
}


int main()
{
	//函数有缺省值，函数调用不用实参
	fun();
	//部分指定，可以只写没有缺省值的参数
	fun2(54,'y');
	// 有缺省值，传参数会覆盖掉缺省值
	fun(50,'r');
	//有函数原型的，缺省值写在函数原型中
	fun3();
	return 0;
}

void fun3(int a , float g )
{
	cout << a <<' ' << g << endl;
}
```

### 函数重载

同一作用域内，函数名字相同，参数列表不同（参数类型或参数个数不同）

c语言中，不允许函数名字相同

```c++
#include <iostream>
using namespace std;

//函数参数列表不同，就可以自动识别
void show(int a )
{
	cout << a << endl;
}

void show(float f )
{
	cout << f << endl;
}

void show(char c)
{
	cout << c << endl;
}

int main()
{
	//76.65默认是double类型的
	show(23);
	show(43.56f);
	show('h');
	return 0;
}
```

函数返回值不作为函数重载的条件

```c++
int fun(int a)
void fun(int a)
    //会报错
```

### 类

```c++
#include <iostream>
using namespace std;

class Cpeople
{
public:
	int a;
	void fun()
	{
		cout << a << endl;
	}
};

int main()
{
	//申请一个对象
	Cpeople op;
	op.a = 15;
	op.fun();

	Cpeople *op1 = new Cpeople;
	op1->a  = 56;
	op1->fun();
	delete op1;

	return 0;
}
```

### 友元

- 友元函数，不相关的函数去使用类内私有成员
- 友元类，不同类使用另一个类私有成员

![image-20211004120911813](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211004120911813.png)



```c++
#include <iostream>
using namespace std;

class Cpeople
{
public:
	int a;
private:
	void fun()
	{
		a = 54;
		cout << a << endl;
	}
protected:
	void fun_pro()
	{
		a = 54;
		cout << a << endl;
	}

	friend void fun2();
	friend int main();
	friend class CP;
};

//子类
class Cchild : public Cpeople
{
	public:
	void fun6()
	{
		fun_pro();
	}
};

void fun2()
{
	Cpeople op2;
	op2.fun();
}

class CP
{
public:
	Cpeople op3;
	void fun3()
	{
		op3.fun();
	}

};

int main()
{
	Cpeople op;
	op.fun();

	CP op4;
	op4.fun3();

	Cchild op_child;
	op_child.fun6();
	return 0;
}
```

类和int一样，都是一种数据类型。只有用类声明对象时，才会开辟出一块空间

### 成员函数

#### 构造函数：自动调用

在对象创建时候，调用。作用，==初始化类内的变量，赋值==。不要在构造函数内部加不相干的代码

```c++
#include <iostream>
using namespace std;

class CStu
{
public:
	int a;
	float f;

	//gou zao function
	CStu()
	{
		a = 14;
		f = 53.98f;
	}
};

int main()
{

	CStu student1;
	
	CStu *stu2 = new CStu;

	cout << stu2->f << endl;

	cout << student1.a <<' '<< student1.f << endl;
	return 0;
}
```

**==类中的函数，可以类内声明，类外定义==**

```C++
//学生类
#include <iostream>
#include <string>
using namespace std;
//设计一个学生类，属性有姓名和学号，可以给其赋值，可以显示

class Cstudent
{
    //属性，成员变量
public:
    string stu_name;
    int stu_id;
    //行为，成员函数，成员方法
public:
    void show()
    {
        cout << "The name of the student：" << stu_name <<endl;
        cout << "The id of the student：" << stu_id <<endl;
    }
    void set_name(string name)
    {
        stu_name = name;
    }
    void set_id(int id)
    {
        stu_id = id;
    }
};


int main()
{

    Cstudent stu;
//    stu.stu_name = "pp";
//    stu.stu_id = 13;
    stu.set_id(15);
    stu.set_name("张三");

    stu.show();
    return 0;
}

```

#### 成员属性私有化

用公共的函数接口来访问

```c++
#include <iostream>
#include <string>
using namespace std;

class Cperson
{
public:
    void set_name(string name)
    {
        C_name = name;
    }
    string get_name()
    {
        return C_name;
    }
    int get_age()
    {
        C_age = 18;
        return C_age;
    }
private:
    //property
    string C_name;//可读可写
    int C_age;//read only
    string C_sex;//read only

};

int main()
{
    Cperson person1;
    person1.set_name("张三");
    cout << "The name is " << person1.get_name() << endl;
    cout << "The age is " << person1.get_age() << endl;
    return 0;
}

```

### this指针

==对象存在，this指针才存在==

**==this指针的作用域在类内，系统默认传递给函数的隐含参数,只能在类内成员函数内部使用==**

```c++
#include <iostream>
using namespace std;

class Cstu
{
public:
    int a;

public:
    void show()
    {
        cout << a << endl;
    }
  //construct function
  //C语言中，相同的变量，会把前一个屏蔽掉
    Cstu(int a)
    {
        this->a = a; //相当于a给自己赋值
        this->show();
    }
    //this指针是Cstu*类型的，指向这个对象，用this指针访问类内成员

    Cstu* getaddr()
    {
        return this;
    }

};

int main()
{
    Cstu stu1(12);
    stu1.show();
    Cstu*p =  stu1.getaddr();
    cout << p <<endl; //也可以使用p去调用类内的函数
    p->show();
    //this->show();//错误写法

    Cstu stu2(17);
    Cstu*p2 = stu2.getaddr();
    cout << p2 << endl;
    return 0;
}

```

### static&const

==static可以使用类名作用域调用，说明是存在于类中的，和对象没有关系，没有声明对象时，也存在静态成员，在创建类的时候就给静态成员分配了空间。是类本身的属性，和对象没有关系==

只有静态常量整型数据成员才能在类中初始化

静态函数             常函数

静态变量             常变量

```c++
#include <iostream>
using namespace std;

class Cstu
{
public:
	static int a;  //initialize in class out
	//int b = 15; 错误写法
	static const int b = 17; //只有静态整型常量数据类型可以在类内初始化
	Cstu()
	{
		a = 12;
	}
};

int Cstu::a = 19;

int main()
{
	
	//static 调用
	//类名作用域
	cout << Cstu::a << endl;
	Cstu stu1;
	cout << stu1.a << endl;

	cout << stu1.b ;
    return 0;
}

------------------------------------------------------------------
#include <iostream>
using namespace std;

class Cstu
{
public:
	static int a;  //initialize in class out
	//int b = 15; 错误写法
	//static const int b = 17; //只有静态整型常量数据类型可以在类内初始化
	static void fun()
	{
		cout << "I am static function." << endl;
	}
	void fun2()
	{
		cout << "I am  function." << endl;
	}
	Cstu()
	{
		a = 12;
	}
};

int Cstu::a = 19;

int main()
{
	
	//static 调用
	//类名作用域
	cout << Cstu::a << endl;
	Cstu::fun();
	Cstu::fun2();//错误
	Cstu stu1;
	cout << stu1.a << endl;
	stu1.fun();

	// cout << stu1.b ;
    return 0;
}

```

```c++
#include <iostream>
using namespace std;

class Cperson
{
public:
	/*Cperson()
	{
		cout << "Cperson的默认构造函数" << endl;
	}*/
	~Cperson()
	{
		cout << "Cperson的默认析构函数" << endl;
	}
	Cperson(int age)
	{
		c_age = age;
		cout << "Cperson的有参构造函数" << endl;
	}
	/*Cperson(const Cperson& a)
	{
		c_age = a.c_age;
		cout << "cperson的拷贝构造函数" << endl;
	}*/
	int c_age;
};

void test01()
{
	Cperson per1(13);
	//per1.c_age = 19;

	Cperson per2(per1);

	cout << "age of per2 is " << per2.c_age << endl;

}

void test02()
{
	Cperson per3(98);  //调用有参构造函数

	Cperson per4(per3); //会调用拷贝构造函数

	cout << "age of per4 is " << per4.c_age << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0
}
```

### 浅拷贝&深拷贝

**==如果属性由在堆区开辟的，一定要自己提供拷贝构造函数，放置浅拷贝带来的问题==**

```c++
#include <iostream>
using namespace std;

class Cperson
{
public:
	Cperson()
	{
		cout << "Cperson的默认构造函数" << endl;
	}
	~Cperson()
	{
		//堆区释放
		if (c_height != NULL)
		{
			delete c_height;
			//c_heignt = NULL;
		}
		cout << "Cperson的默认析构函数" << endl;
	}
	Cperson(int age, int height)
	{
		c_height = new int(height);

		c_age = age;
		cout << "Cperson的有参构造函数" << endl;
	}
	//浅拷贝带来异常
	//以下为深拷贝
	Cperson(const Cperson& a)
	{

		/*默认构造函数的操作
		c_age = a.c_age;
		c_height = a.c_height;*/
		//自己写一个构造函数,在堆区重新开辟一块空间
		c_age = a.c_age;
		c_height = new int(*a.c_height);
		cout << "cperson的拷贝构造函数" << endl;
	}
public:
	int c_age;
	int *c_height;
};

void test01()
{
	Cperson per1(19,179);
	//per1.c_age = 19;

	Cperson per2(per1);

	cout << "age of per1 is " << per1.c_age << 
		    "height of per1 is " << *per1.c_height << endl;

	cout << "age of per2 is " << per2.c_age << 
		    "height of per2 is " <<  *per2.c_height << endl;

}



int main()
{
	test01();

	system("pause");
	return 0;
}
```

#### 构造函数初始化列表

- Cperson()：C_a(a),C_b(b),C_c(c)

```c++
#include <iostream>
using namespace std;


class Cperson
{
	//构造函数
	//传统初始化方法
public:
	/*Cperson(int a,int b,int c)
	{
		C_a = a;
		C_b = b;
		C_c = c;
	}*/
	Cperson(int a,int b,int c) : C_a(a),C_b(b),C_c(c)
	{

	}
public:
	int C_a;
	int C_b;
	int C_c;
};

//void test01()
//{
//	Cperson per1(23,13,25);
//	cout << "C_a: " << per1.C_a <<endl;
//	cout << "C_b: " << per1.C_b <<endl;
//	cout << "C_c: " << per1.C_c <<endl;
//}


void test02()
{
	Cperson per2(45,76,43);
	cout << "C_a: " << per2.C_a <<endl;
	cout << "C_b: " << per2.C_b <<endl;
	cout << "C_c: " << per2.C_c <<endl;
}

int main()
{
	//test01();
	test02();
	system("pause");
	return 0;
}
```

### 类作对象

==构造函数的顺序是：先构造内层的，在构造外层的，析构函数的执行顺序服从“先进后出”的规则，与构造函数顺序相反。==

```c++
#include <iostream>
using namespace std;
#include <string>


//手机类
class Cphone
{
public:
	//构造函数
	Cphone(string name)
	{
		cout << "phone" << endl;
		C_PhoneNmae = name;
	}
	~Cphone()
	{
		cout << "phone destructor" << endl;
	}
public:
	//手机品牌
	string C_PhoneNmae;

};


//人类
class Cperson
{
public:
	//属性
	string c_name;
	Cphone c_phone;
public:
	Cperson(string name,string phone):c_name(name),c_phone(phone)
	{
		cout << "person " << endl;
	}
	~Cperson()
	{
		cout << "person destructor" << endl;
	}
};

void test01()
{
	Cperson per1("zhangsan","xiaomi");
	cout << per1.c_name << " have " << per1.c_phone.C_PhoneNmae << endl;
}


int main()
{
	test01();
	system("pause");
	return 0;
}
```

![image-20211018233256498](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211018233256498.png)

```c++
#include <iostream>
using namespace std;

class Cperson
{
public:
	int c_age; //非静态成员变量，属于类的对象
	static int c_name; //静态成员函数变量，不属于类的对象
	
	void fun() //非静态成员函数，不属于类的对象
	{

	}
	static void fun1() {} //静态成员函数，属于类的对象

};

void test01()
{
	Cperson per1;
	cout << "size of per1 is " << sizeof(per1) << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

### 空指针访问成员函数

类中的成员属性默认在前面有<kbd>this-></kbd>.而<kbd>person*p = NULL</kbd>语句并没有创建对象，所以是无法访问对象的，所以this指针是不存在的，

```c++
#include <iostream>
using namespace std;

class Cperson
{
public:
	int c_age;
	void showName()
	{
		cout << "this is the class name" << endl;

	}
	//由于没有创建对象，使用this指针产生异常
	void showAge()
	{
		if (this == NULL)
		{
			return;
		}
		cout << this->c_age << endl;
	}
};


void test01()
{
	Cperson *p = NULL;
	//p->showAge();
	p->showName();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

```c++
#include <iostream>
using namespace std;
#include <string>

//class CBuilding; //goodgay中使用了building类，因此要先声明一下，让编译器认识，类似于函数声明
/*-----------------Building class------------------------*/
//建筑类
class CBuilding
{
public:
	CBuilding();
public:
	string c_livingroom;
private:
	string c_bedroom;

	friend class CGoodgay;//友元类
    friend void goodgay::visit();//友元成员函数
};

//构造函数，类内声明，类外定义，要声明是哪个类的构造函数
CBuilding::CBuilding()
{
	c_livingroom = "living room";
	c_bedroom = "bed room";
}

/*----------------Googgay class-----------------------------*/
class CGoodgay
{
public:
	CBuilding * building1;
	CGoodgay();
	void visit();
};
//构造函数，初始化成员变量
CGoodgay::CGoodgay()
{
	building1 = new CBuilding;
}

void CGoodgay::visit()
{
	cout << "Good gay is looking at " << building1->c_livingroom << endl;

	cout << "Good gay is looking at " << building1->c_bedroom << endl;
}

/*-------------------test-------------------------------*/


void test01()
{
	CGoodgay gay1;
	gay1.visit();
}
/*-----------------main function-----------------------*/
int main()
{
	test01();
	system("pause");
	return 0;
}
```

![image-20211019172544775](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211019172544775.png)

![image-20211019172649352](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211019172649352.png)

### 运算符重载

![image-20211019233541178](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211019233541178.png)

```c++
#include <iostream>
using namespace std;

class CPerson
{
	public://成员函数重载+
		CPerson operator+(CPerson &p)
		{
			CPerson temp;
			temp.c_a = this->c_a + p.c_a;
			temp.c_b = this->c_b + p.c_b;
			return temp;
		}
public:
	int c_a;
	int c_b;
};



void test01()
{
	CPerson per1;
	per1.c_a = 34;
	per1.c_b = 54;
	CPerson per2;
	per2.c_a = 54;
	per2.c_b = 74;
	CPerson per3;

	per3 = per1 + per2;

	cout << "per3.c_a =" << per3.c_a << endl;
	cout << "per3.c_b =" << per3.c_b << endl;
}

////全局函数重载+
//CPerson operator+ (CPerson &p1, CPerson &p2)
//{
//	CPerson temp;
//	temp.c_a = p1.c_a + p2.c_a;
//	temp.c_b = p1.c_b + p2.c_b;
//	return temp;
//}
   //成员函数重载本质调用
	Cperson p3 = p1.operator+(p2)
	简写：p3 = p1+p2;
	全局函数重载本质调用
	Cperson p3 = operator+(p1,p2)
	简写: p3 = p1+p2
int main()
{
	test01();
	system("pause");
	return 0;
}
```

```c++
#include <iostream>
using namespace std;

class Cperson
{
public:
	int c_a;
	int c_b;
	Cperson()
	{
		c_a = 89;
		c_b = 93;
	}
};

ostream & operator<<(ostream &cout ,Cperson &p)
{
	cout << "c_a: " << p.c_a  << endl;
	cout << "c_b: " << p.c_b << endl;
	return cout;
}

void test01()
{
	Cperson per1;

	cout << per1 << endl;
	//cout << per1 <<endl;无限追加输入，是因为链式编程思想
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```



### 递增运算符重载

![image-20211020135253168](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020135253168.png)





### 继承

好处：减少重复的代码

语法：<kbd>class 子类:继承方式 父类</kbd>

子类又叫派生类

- 从父类继承过来的
- 自己新增的

父类又叫基类

![image-20211020164955371](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020164955371.png)

父类中的非静态成员变量都会被继承下去，无论是否私有还是公有

子类与父类中的同名函数，同名变量。默认会调用子类中的，子类中的会隐藏掉父类中所有的同名函数

![image-20211020174208051](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020174208051.png)

```c++
#include <iostream>
using namespace std;

class CFather
{
public:
	CFather()
	{
		c_a = 34;
	}
public:
	int c_a;
};

class CSon :public CFather
{
public:
	int c_a;

	CSon()
	{
		c_a = 56;
	}
};

void test01()
{
	CSon son1;
	cout << son1.c_a << endl;
	cout << son1.CFather::c_a << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

![image-20211020214242953](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020214242953.png)

### 多态

![image-20211020220806664](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020220806664.png)

重载：函数名相同，参数不同

重写：函数返回值，函数名，形参列表都相同

![image-20211020221534209](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020221534209.png)

![image-20211020221707835](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020221707835.png)

![image-20211020221741333](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211020221741333.png)

==成员函数不属于对象==

==不管是什么类型的指针，都占4个字节==

![image-20211021202239635](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021202239635.png)

![image-20211021202658926](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021202658926.png)

![image-20211021203623112](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021203623112.png)

![image-20211021203952490](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021203952490.png)

![image-20211021204111880](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021204111880.png)

**==通过父类的指针，可以调用不同的子类对象的函数或成员==**

![image-20211021220439165](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021220439165.png)

![image-20211021221722313](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021221722313.png)

![image-20211021225354564](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021225354564.png)

![image-20211021225639639](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021225639639.png)

![image-20211021230353091](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021230353091.png)

![image-20211021230635796](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021230635796.png)

![image-20211021231644579](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211021231644579.png)

![image-20211022105401533](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211022105401533.png)

![image-20211022110526056](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211022110526056.png)

![image-20211022111543036](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211022111543036.png)

![image-20211022111709836](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211022111709836.png)

![image-20211022121233984](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211022121233984.png)

![image-20211024224340411](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224340411.png)

![image-20211024224522966](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224522966.png)

![image-20211024224613026](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224613026.png)

![image-20211024224747037](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224747037.png)

![image-20211024224808615](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224808615.png)

![image-20211024224924888](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211024224924888.png)

==**接口都是一样的，由于对象不同，就显示出多态的意义了**==

一个接口，有多种形态

![image-20211026102816318](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026102816318.png)

![image-20211026103235801](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026103235801.png)

![image-20211026103307827](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026103307827.png)

![image-20211026170316284](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026170316284.png)

![image-20211026170448680](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026170448680.png)

![image-20211026170501131](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026170501131.png)

![image-20211026172757953](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026172757953.png)

![image-20211026173241390](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026173241390.png)

![image-20211026174105364](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026174105364.png)

### 如何判断数据是否为空

**EOF文件的结尾**

![image-20211026174241876](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026174241876.png)

![image-20211026174807707](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026174807707.png)

![image-20211026224231250](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026224231250.png)

![image-20211026224303886](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026224303886.png)

![image-20211026224329145](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026224329145.png)

![image-20211026230436353](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026230436353.png)

![image-20211026230456972](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211026230456972.png)

![image-20211027092044192](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211027092044192.png)

![image-20211027092222524](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211027092222524.png)

![image-20211027092242701](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211027092242701.png)

![image-20211027105929960](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211027105929960.png)

![image-20211027105946262](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211027105946262.png)

## 模板

![image-20211030172724604](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211030172724604.png)

![image-20211030173054674](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211030173054674.png)

![image-20211030173746509](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211030173746509.png)

![image-20211031101246245](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031101246245.png)

![image-20211031101741998](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031101741998.png)

![image-20211031104651606](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031104651606.png)

![image-20211031104853068](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031104853068.png)

![image-20211031110403838](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031110403838.png)

![image-20211031110431568](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031110431568.png)

![image-20211031110841773](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031110841773.png)

![image-20211031111537579](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031111537579.png)

![image-20211031112511357](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031112511357.png)

![image-20211031112810468](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031112810468.png)

![image-20211031112838946](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211031112838946.png)

# 算法

### 冒泡排序

![image-20211110222527770](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211110222527770.png)

![image-20211110224058824](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20211110224058824.png)

