

# 

[TOC]



## C++指针

在c++中&和*是与指针密切相关的两个操作符，但它们各自扮演者不同的角色。

**1、& 操作符（取地址操作符）：**

**&**操作符用于获取一个变量的内存地址。当你对一个变量使用&操作符时，它会返回该变量的地址，这个地址是一个指针类型的值。

**2、*操作符（解引用操作符或间接成员访问操作符）：**

当*用在指针前时，它用作解引用操作符，即它获取指针所指向地址中的值。

例如，如果你有一个指针int* ptr=&x;(这里x是之前定义的变量)，那么 *ptr 将访问ptr指向的内存位置中的值，即x的值，也就是10。

**关系：**

简而言之，&用于获取地址（生成指针），而*用于访问指针所指向地址中的值（解引用指针）。

```c++
#include <iostream>
int main() {
	int x = 10;
	int* ptr = &x;			// 使用&获取x的地址，并将该地址赋值给ptr

	std::cout << "x的值是：" << x << std::endl;		// 直接访问x
	std::cout << "通过ptr访问x的值是：" << *ptr << std::endl;		// 通过ptr解引用访问x

	*ptr = 20; // 通过ptr修改x的值
	std::cout << "修改后x的值是：" << x << std::endl;	//	验证x的值是否已改变
	return 0;
}

// // 输出结果：
// // x的值是：10
// // 通过ptr访问x的值是：10
// // 修改后x的值是：20
```

指针是一个变量，其值为另一个变量的地址，即，内存位置的直接地址。就像其他变量和常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。指针变量声明的一般形式为：

```c++
type *var-name;
```



每一个变量都有一个内存位置，每一个位置都定义了可使用的连字号（&）运算符访问的地址，他表示了在内存中的一个地址。请看下面这个实例，它将输出定义的变量地址：

```c++
#include <iostream>

using namespace std;

int main() {
	int var1;
	char var2[10];

	cout << "var1变量的地址是：" << &var1 << endl;

	cout << "var2变量的地址是：" << &var2 << endl;
}
```

```c++
#include <iostream>
using namespace std;
int main() {
	int var = 20;			//实际变量的声明
	int* ip;					//指针变量的命名

	ip = &var;			//在指针变量中存储var的地址

	cout << "Value of var variable：" << var << endl;

	// 输出指针变量中存储的地址
	cout << "Address stored in ip variable：" << ip << endl;
	// 访问指针中地址的值
	cout << "Value of *ip variable：" << *ip << endl;
	return 0;
}

输出结果：
Value of var variable：20
Address stored in ip variable：00000047A04FF5E4
Value of *ip variable：20
```

**指针值：**指针值是指针变量本身存储的值。这是一个内存地址，它指向了程序中某个位置。

在这个例子中，a是一个指针，他的指针值是&b，即变量b的地址，a现在 ”知道'' 在哪里可以找到b的值

```c++
int b = 5;
int* a =&b
```

**指向值：**指向值是指针所指向的内存地址中存储的数据值，换句话说，他是通过解引用指针（使用*操作符）得到的值

c是指向值；

```c++
int b = 5;
int* a = &b;
int c = *a;
```

## c++指针详解

### c++空指针

在变量声明的时候，如果没有确切的地址可以赋值，为指针变量赋一个NULL值是一个良好的编程习惯，赋值为NULL的指针被称为空指针。

NULL指针是一个定义在标准库中的值为零的常量。请看下面的程序：

```c++
#include <iostream>
using namespace std;
int main() {
	int* ptr = NULL;
	cout << "ptr的值为：" << ptr;
	return 0;
}
```

### C++指针的算数运算

**递增一个指针：**

在c++中，指针是一个变量，他存储一个内存地址。递增一个指针意味着将指针指向下一个内存位置，这通常是指向下一个数组元素。递增一个指针会根据指针所指向的数据类型自动调整指针的值。

**例如：**如果指针指向一个int类型的数组元素，那么递增指针将使值指向下一个int元素

```c++
#include <iostream>

int main() {
	// 定义一个数组
	int arr[] = { 1,2,3,4,5 };

	// 定义一个指向数组第一个元素的指针
	int* ptr = arr;
	std::cout << "指针当前指向的元素：" << *ptr << std::endl;
	// 递增指针
	ptr++;
	// 输出指针指向的元素
	std::cout << "递增指针后指向的元素：" << *ptr << std::endl;
	return 0;
}
```

**递减一个指针：**

在c++中，指针不仅可以递增，也可以递减。递减一个指针意味着将指针向前一个内存位置。与递增指针类似，递减指针也会根据指针所指向的数据类型自动调整指针的值。

```c++
#include <iostream>
int main() {
	// 定义一个数组
	int arr[] = { 1,2,3,4,5 };
	// 定义一个指向数组第二个元素的指针
	int* ptr = &arr[1];
	// 输出指针当前的元素
	std::cout << "指针当前指向的元素：" << *ptr << std::endl;
	//递减指针
	ptr--;
	// 输出指针递减后指向的元素
	std::cout << "递减指针后指向的元素：" << *ptr << std::endl;
	return 0;
}
```

**指针的比较**

在c++中，指针的比较操作可以用于确定两个指针是否指向相同位置、一个指针是否指向的位置在另一个指针或者之后等。指针的比较主要包括一下几种：

1、相等性比较（  ==   和  ！=  ）

2、关系比较（<，<=，>，>=）

相等性比较：

```c++
#include <iostream>
int main() {
	int a = 10;
	int b = 20;
	int* ptr1 = &a;
	int* ptr2 = &a;
	int* ptr3 = &b;

	// 比较指针是否相等
	if (ptr1 == ptr2) {
		std::cout << "ptr1 和 ptr2 指向相同的位置" << std::endl;
	}
	else {
		std::cout << "ptr1 和 ptr2 指向不同的位置" << std::endl;
	}
	if (ptr1 != ptr3) {
		std::cout << "ptr1 和 ptr3 指向不同的位置" << std::endl;
	}
	else {
		std::cout << "ptr1 和 ptr3 指向相同的位置" << std::endl;
	}
	return 0;
}
```

关系比较：

```c++
#include <iostream>
int main() {
	int arr[] = { 1,2,3,4,5 };
	int* ptr1 = &arr[1];
	int* ptr2 = &arr[3];

	//比较指针的相对位置
	if (ptr1 < ptr2) {
		std::cout << "ptr1 指向的元素在 ptr2 指向的元素之前" << std::endl;
	}
	else {
		std::cout << "ptr1 指向的元素不在 ptr2 指向的元素之前" << std::endl;
	}
	return 0;
}
```



### C++指针  vs  数组

指针和数组是密切相关的。事实上，指针和数组在很多情况下是可以互换的。例如，一个指向数组开头的指针，可以通过指针的算数运算或数组索引来访问数组。

```c++
#include <iostream>

using namespace std;
const int MAX = 3;
int main() {
	int var[MAX] = { 10,100,200 };
	int* ptr;

	// 指针中的数组地址
	ptr = var;
	for (int i = 0; i < MAX; i++) {
		cout << "var[" << i << "]的内存地址为 ";
		cout << ptr << endl;

		cout << "var[" << i << "]的值为 ";
		cout << *ptr << endl;
		// 移动到下一个位置
		ptr++;
	}
	return 0;
}


输出结果：
var[0]的内存地址为 000000A4D66FF528
var[0]的值为 10
var[1]的内存地址为 000000A4D66FF52C
var[1]的值为 100
var[2]的内存地址为 000000A4D66FF530
var[2]的值为 200
```

指针和数组并不是完全互换的

```c++
#include <iostream>
using namespace std;
const int MAX = 3;
int main() {
	int var[MAX] = { 10,100,200 };
	for (int i = 0; i < MAX; i++) {
		*var = i;		// 正确的语法
		var++;			//  错误的语法
	}
	return 0;
}
```

### C++指针数组

**实例：**

```c++
#include <iostream>
 
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
 
   for (int i = 0; i < MAX; i++)
   {
      cout << "Value of var[" << i << "] = ";
      cout << var[i] << endl;
   }
   return 0;
}

输出结果：
Value of var[0] = 10
Value of var[1] = 100
Value of var[2] = 200

```

可能有一种情况，我们想要让数组存储指向int或char或其他数据类型指针：

```c++
int* ptr[MAX];
```

在这里，把ptr声明成为一个数组，由MAX个整数指针组成。因此，ptr中的每个元素，都是一个指向int值的指针。下面的实例用到了三个整数，它们将存储在一个指针数组中：

```c++
#include <iostream>
using namespace std;
const int MAX = 3;
int main() {
	int var[MAX] = { 10,100,200 };
	int* ptr[MAX];

	for (int i = 0; i < MAX; i++) {
		ptr[i] = &var[i];    //  赋值为整数的地址
	}
	for (int i = 0; i < MAX; i++) {
		cout << "Value of var[" << i << "] = " << *ptr[i] << endl;  // 地址的值
		cout << "Address of var[" << i << "]=  " << ptr[i] << endl; // 地址
	}
	return 0;
}


输出结果：
Value of var[0] = 10
Address of var[0]=  00000046DC2FF8B8
Value of var[1] = 100
Address of var[1]=  00000046DC2FF8BC
Value of var[2] = 200
Address of var[2]=  00000046DC2FF8C0
```

您也可以用一个指向字符的指针数组来存储一个字符串列表：

```c++
#include <iostream>
using namespace std;
const int MAX = 4;
int main() {
	const char* name[MAX]{
		"Zara Ali",
		"Hina Ali",
		"Nuha Ali",
		"Sara Ali",
	};
	for (int i = 0; i < MAX; i++) {
		cout << "Value of name[" << i << "] = " << name[i] << endl;
	}
	return 0;
}
```

### C++指向指针的指针（多级间接寻址）

当一个目标值被一个指针间接指向到另一个指针时，访问这个值需要使用两个星号运算符

```c++
#include <iostream>
using namespace std;

int main() {
	int var;
	int* ptr;
	int** pptr;

	var = 3000;

	// 获取var的地址
	ptr = &var;

	// 使用运算符 & 获取 ptr 的地址
	pptr = &ptr;

	cout << "var 值为：" << var << endl;
	cout << "*ptr 值为：" << *ptr << endl;
	cout << "**pptr 值为：" << **pptr << endl;
	return 0;
}
```

### C++ 传递指针给函数

c++允许您传递指针给函数，只需要简单地声明函数参数为指针类型即可。

下面的实例中，我们传达一个无符号的log型指针给函数，并在函数内改变这个值；

**实例：**

```c++
#include <iostream>
#include <ctime>
using namespace std;

// 在写函数时应该习惯性的先声明函数，然后在定义函数
void getSecounds(unsigned long* par);

void getSecounds(unsigned long* par) {
	// 获取当前秒数
	*par = time(NULL);
	return;
}

int main() {
	unsigned long sec;
	getSecounds(&sec);
	//输出实际值
	cout << "Number of secound:  " << sec << endl;
	return 0;
}
```

能接受指针作为参数的函数，也能接收数组作为参数，如下所示

```c++
#include <iostream>
using namespace std;

// 函数声明
double getAverage(int* arr, int size);

double getAverage(int* arr, int size) {
	int i, sum = 0;
	double avg;
	for (i = 0; i < size; ++i) {
		sum += arr[i];
	}
	avg = double(sum) / size;
	return avg;
}

int main() {
	// 带有5个元素的整数型数组
	int balance[5] = { 1000,2,3,17,50 };
	double avg;

	// 传递一个指向性数组的指针作为参数
	avg = getAverage(balance, 5);
	cout << "Average value is:  " << avg << endl;
	return 0;
}
```

### C++ 从函数返回指针

C++ 不支持在函数外返回局部变量的地址，除非定义局部变量为static变量。

```c++
#include <iostream>
#include <ctime>
#include <cstdlib>

using namespace std;

int* getRandom() {
	static int r[10];

	// 设置种子
	srand((unsigned)time(NULL));
	for (int i = 0; i < 10; ++i) {
		r[i] = rand();
		cout << r[i] << endl;
	}
	return r;
}
int main() {
	// 一个指向整数的指针
	int* p;
	p = getRandom();
	for (int i = 0; i < 10; i++) {
		cout << "*(p+" << i << ") :  ";
		cout << *(p + i) << endl;
	}
	return 0;
}


// 输出结果
16083
21495
16016
14313
15074
21914
2168
23799
30112
4323
*(p+0) :  16083
*(p+1) :  21495
*(p+2) :  16016
*(p+3) :  14313
*(p+4) :  15074
*(p+5) :  21914
*(p+6) :  2168
*(p+7) :  23799
*(p+8) :  30112
*(p+9) :  4323
```

### C++ 常量指针、指针常量、常量指针常量

- **常量指针**：常量指针是指一个指针，它指向一个常量（即该指针所指向的内存区域中的数据是常量，不能被修改）。但是，常量指针本身的值（即它所指向的内存地址）是可以被改变的。

- **指针常量**：指针常量是指一个指针，它的值（即它所指向的内存地址）在初始化之后就不能被改变。换句话说，指针本身是一个常量，但其指向的内容（即该地址上的数据）是可以被修改的。

- **常量指针常量**：两者都不可以修改。

```c++
#include <iostream>
using namespace std;

int main() {
	int a = 1;
	int b = 2;
	int* c = &a;
	cout << "地址：" << c << "  指向的值：" << *c << endl;
	// 常量指针，表示被指针指向的常量，指向的值不能修改，指向可以改
	const int* d = &a;
	cout << "开始的地址：" << d << "  开始指向的值：" << *d << endl;
	// 错误的
	//*d = 2;
	// 修改指向
	d = &b;
	cout << "修改后的地址：" << d << "  修改后指向的值：" << *d << endl;
	// 指针常量，表示指针指向的值是一个常量，指向的值可以改，地址不可以改
	int* const e = &a;
	cout << "开始的地址：" << e << "开始的指向的值：" << *e << endl;
	*e = 20;
	cout << "修改后的地址：" << e << "  修改后指向的值：" << *e << endl;
}
```

## 

## 面向对象

```c++
class classname
{
    Access specifiers:		<-// 访问控制符：public / private / protected 
    	    type value;     <-// 变量
             Member functions(){
                // 方法
            }
};		<-// 分号结束一个类
```

**例如：**

```c++
class Box
{
private:
	int l = 1;
	int b = 2;
	int h = 3;
public:
	int getArea() {
		return (l * b * h);
	}
};
```

**定义c++对象：**

```c++
Box Box1;	// 声明Box1，类型为 Box
Box Box2;	// 声明Box2, 类型为 Box
```

**实例：**

```c++
#include <iostream>
using namespace std;

class Box
{ 
public:
	double length;	// 长度
	double breadth;	// 宽度
	double height;		// 高度
	// 成员函数说明
	double get(void);
	void set(double len, double bre, double hei);
};
// 成员函数定义
double Box::get(void) {
	return length * height * breadth;
}
void Box::set(double len, double bre, double hei) {
	length = len;
	breadth = bre;
	height = hei;
}
int main()
{
	Box Box1;
	Box Box2;
	Box Box3;
	double volume = 0.0;	// 用于存储体积
	// box1
	Box1.height = 5.0;
	Box1.breadth = 6.2;
	Box1.length = 9.9;
	// box2
	Box2.height = 6.3;
	Box2.breadth = 8.2;
	Box2.length = 7.7;
	
	volume = Box1.length * Box1.breadth * Box1.height;
	cout << "Box1的体积是：" << volume << endl;

	volume = Box2.height * Box2.length * Box2.breadth;
	cout << "Box2的体积是：" << volume << endl;

	// box3
	Box3.set(16.0, 11.2, 25.3);
	volume = Box3.get();
	cout << "Box3的体积是：" << volume << endl;
	return 0;
}
```
