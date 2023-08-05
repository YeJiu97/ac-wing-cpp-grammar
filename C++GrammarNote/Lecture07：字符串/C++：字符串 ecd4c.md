# C++：字符串

## C语言中的字符串

C++提供了两种类型的字符串：

1. c风格的字符串
2. C++引入的string类类型

C风格的字符串起源于C语言，并且在C++语言中得到了支持。

字符串实际上是用null字符\0终止的一维字符数组。因此，一个以 null 结尾的字符串，包含了组成字符串的字符。

我们可以尝试一下：

```cpp
#include <iostream>
 
using namespace std;
 
int main ()
{
   char site[7] = {'A', 'B', 'C', 'D', 'E', 'F', '\0'};
   cout << site << endl;
 
   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```cpp
ABCDEF
```

C++提供了大量的相关的函数：

![Untitled](C++%EF%BC%9A%E5%AD%97%E7%AC%A6%E4%B8%B2%20ecd4c/Untitled.png)

我们可以随便测试一下：

```cpp
#define _CRT_SECURE_NO_DEPRECATE

#include <iostream>
#include <cstring>
using namespace std;

int main()
{
	char site[7] = { 'A', 'B', 'C', 'D', 'E', 'F', '\0'};

	char site2[7] = {'1', '2', '3','4', '5', '6', '\0'};

	strcpy(site, site2);

	cout << site << endl;

	return 0;
}
```

运行的结果为：

```cpp
123456
```

## **C++ 中的 String 类**

C++ 标准库提供了 **string**类类型，支持上述所有的操作，另外还增加了其他更多的功能。

我们可以尝试一下：

```cpp
#include <iostream>
#include <string>
 
using namespace std;
 
int main ()
{
   string str1 = "baidu";
   string str2 = "google";
   string str3;
   int  len ;
 
   // 复制 str1 到 str3
   str3 = str1;
   cout << "str3 : " << str3 << endl;
 
   // 连接 str1 和 str2
   str3 = str1 + str2;
   cout << "str1 + str2 : " << str3 << endl;
 
   // 连接后，str3 的总长度
   len = str3.size();
   cout << "str3.size() :  " << len << endl;
 
   return 0;
}
```

运行的结果为：

```cpp
str3 : baidu
str1 + str2 : baidugoogle
str3.size() :  11
```

compare函数：

```cpp
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string str1 = "123";
	string str2 = "456";
	int result = str1.compare(str2);
	cout << result << endl;

	return 0;
}
```

运行结果为：

```cpp
-1
```

compare的原理为：两个字符串自左向右逐个字符相比（按ASCII值大小相比较），直到出现不同的字符或遇’\0’为止。

substr 成员函数可以用于求子串 (n, m)，原型如下：

```cpp
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string s1 = "this is ok";
	string s2 = s1.substr(2, 4);  // s2 = "is i"

	cout << s2 << endl;

	return 0;
}
```

结果为：

```cpp
is i
```

或者我们可以直接交换两个字符串：

```cpp
#include <iostream>
#include <string>

using namespace std;

int main()
{
	string s1("West"), s2("East");
	s1.swap(s2);  // s1 = "East"，s2 = "West"

	cout << s1 << endl;
	cout << s2 << endl;

	return 0;
}
```

运行的结果为：

```cpp
East
West
```

string 类有一些查找子串和字符的成员函数，它们的返回值都是子串或字符在 string 对象字符串中的位置（即下标）。如果查不到，则返回 string::npos。string: :npos 是在 string 类中定义的一个静态常量。这些函数如下：

- find：从前往后查找子串或字符出现的位置。
- rfind：从后往前查找子串或字符出现的位置。
- find_first_of：从前往后查找何处出现另一个字符串中包含的字符。例如：
- s1.find_first_of("abc"); //查找s1中第一次出现"abc"中任一字符的位置
- find_last_of：从后往前查找何处出现另一个字符串中包含的字符。
- find_first_not_of：从前往后查找何处出现另一个字符串中没有包含的字符。
- find_last_not_of：从后往前查找何处出现另一个字符串中没有包含的字符。

代码为：

```cpp
#include <iostream>
#include <string>
using namespace std;
int main()
{
    string s1("Source Code");
    int n;
    if ((n = s1.find('u')) != string::npos) //查找 u 出现的位置
        cout << "1) " << n << "," << s1.substr(n) << endl;
    //输出 l)2,urce Code
    if ((n = s1.find("Source", 3)) == string::npos)
        //从下标3开始查找"Source"，找不到
        cout << "2) " << "Not Found" << endl;  //输出 2) Not Found
    if ((n = s1.find("Co")) != string::npos)
        //查找子串"Co"。能找到，返回"Co"的位置
        cout << "3) " << n << ", " << s1.substr(n) << endl;
    //输出 3) 7, Code
    if ((n = s1.find_first_of("ceo")) != string::npos)
        //查找第一次出现或 'c'、'e'或'o'的位置
        cout << "4) " << n << ", " << s1.substr(n) << endl;
    //输出 4) l, ource Code
    if ((n = s1.find_last_of('e')) != string::npos)
        //查找最后一个 'e' 的位置
        cout << "5) " << n << ", " << s1.substr(n) << endl;  //输出 5) 10, e
    if ((n = s1.find_first_not_of("eou", 1)) != string::npos)
        //从下标1开始查找第一次出现非 'e'、'o' 或 'u' 字符的位置
        cout << "6) " << n << ", " << s1.substr(n) << endl;
    //输出 6) 3, rce Code
    return 0;
}
```