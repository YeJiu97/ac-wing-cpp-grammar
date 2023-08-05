# C++：运算符

## 运算符

C++支持常用的7种运算符。

假设变量 A 的值为 10，变量 B 的值为 20

![Untitled](C++%EF%BC%9A%E8%BF%90%E7%AE%97%E7%AC%A6%207d0cb/Untitled.png)

测试程序为：

```cpp
#include <iostream>
using namespace std;

int main()
{
	int a = 21;
	int b = 10;
	int c;

	c = a + b;
	cout << "Line 1 - c 的值是 " << c << endl;
	c = a - b;
	cout << "Line 2 - c 的值是 " << c << endl;
	c = a * b;
	cout << "Line 3 - c 的值是 " << c << endl;
	c = a / b;
	cout << "Line 4 - c 的值是 " << c << endl;
	c = a % b;
	cout << "Line 5 - c 的值是 " << c << endl;

	int d = 10;   //  测试自增、自减
	c = d++;
	cout << "Line 6 - c 的值是 " << c << endl;

	d = 10;    // 重新赋值
	c = d--;
	cout << "Line 7 - c 的值是 " << c << endl;
	return 0;
}
```

关于取模%，我们需要额外的注意：

```cpp
#include <iostream>
using namespace std;

int main()
{
	cout << -5 % 2 << endl;
	cout << -5 % -2 << endl;
	cout << 5 % 2 << endl;
	cout << 5 % -2 << endl;

	return 0;
}
```

运行的结果为：

```cpp
-1
-1
1
1
```

从数学上来讲，5/-2=2......-1，因为（-2*2）+（-1）= -5。

但是从计算机的角度来讲，被除数的符号决定了余数的符号。

## 关系运算符

假设变量 A 的值为 10，变量 B 的值为 20，则：

![Untitled](C++%EF%BC%9A%E8%BF%90%E7%AE%97%E7%AC%A6%207d0cb/Untitled%201.png)

程序测试为：

```cpp
#include <iostream>
using namespace std;

int main()
{
    int a = 21;
    int b = 10;
    int c;

    if (a == b)
    {
        cout << "Line 1 - a 等于 b" << endl;
    }
    else
    {
        cout << "Line 1 - a 不等于 b" << endl;
    }
    if (a < b)
    {
        cout << "Line 2 - a 小于 b" << endl;
    }
    else
    {
        cout << "Line 2 - a 不小于 b" << endl;
    }
    if (a > b)
    {
        cout << "Line 3 - a 大于 b" << endl;
    }
    else
    {
        cout << "Line 3 - a 不大于 b" << endl;
    }
    /* 改变 a 和 b 的值 */
    a = 5;
    b = 20;
    if (a <= b)
    {
        cout << "Line 4 - a 小于或等于 b" << endl;
    }
    if (b >= a)
    {
        cout << "Line 5 - b 大于或等于 a" << endl;
    }
    return 0;
}
```

运行结果为：

```cpp
Line 1 - a 不等于 b
Line 2 - a 不小于 b
Line 3 - a 大于 b
Line 4 - a 小于或等于 b
Line 5 - b 大于或等于 a
```

## **逻辑运算符**

假设变量 A 的值为 1，变量 B 的值为 0。

![Untitled](C++%EF%BC%9A%E8%BF%90%E7%AE%97%E7%AC%A6%207d0cb/Untitled%202.png)

测试程序为：

```cpp
#include <iostream>
using namespace std;
 
int main()
{
   int a = 5;
   int b = 20;
   int c ;
 
   if ( a && b )
   {
      cout << "Line 1 - 条件为真"<< endl ;
   }
   if ( a || b )
   {
      cout << "Line 2 - 条件为真"<< endl ;
   }
   /* 改变 a 和 b 的值 */
   a = 0;
   b = 10;
   if ( a && b )
   {
      cout << "Line 3 - 条件为真"<< endl ;
   }
   else
   {
      cout << "Line 4 - 条件不为真"<< endl ;
   }
   if ( !(a && b) )
   {
      cout << "Line 5 - 条件为真"<< endl ;
   }
   return 0;
}
```

运行结果为：

```cpp
Line 1 - 条件为真
Line 2 - 条件为真
Line 4 - 条件不为真
Line 5 - 条件为真
```

## Condition运算符

condition运算符的语法为：

```cpp
Condition ? X : Y
```

这可以被理解为：

```cpp
如果 Condition 为真 ? 则值为 X : 否则值为 Y。
```

程序为：

```cpp
#include <iostream>
using namespace std;

int main()
{
	// 局部变量声明
	int x, y = 10;

	x = (y < 10) ? 30 : 40;

	cout << "value of x: " << x << endl;

	return 0;
}
```

运行的结果为：

```cpp
value of x: 40
```