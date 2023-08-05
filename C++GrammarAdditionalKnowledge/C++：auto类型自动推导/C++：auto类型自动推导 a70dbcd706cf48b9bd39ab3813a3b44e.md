# C++：auto类型自动推导

在 C++11 之前的版本（C++98 和 C++ 03）中，定义变量或者声明变量之前都必须指明它的类型，比如 int、char 等。

在一些比较灵活的语言中，比如 C#、JavaScript、PHP、Python 等，程序员在定义变量时可以不指明具体的类型，而是让编译器（或者解释器）自己去推导，这就让代码的编写更加方便。

C++11 为了顺应这种趋势也开始支持自动类型推导了！C++11 使用 auto 关键字来支持自动类型推导。

使用了 auto 关键字以后，编译器会在编译期间自动推导出变量的类型，这样我们就不用手动指明变量的数据类型了。

我们可以使用int类型进行简单的尝试：

```cpp
#include <iostream>
#include<typeinfo>
using namespace std;

int main() {

	auto num = 123;

	if (typeid(num) == typeid(int)) {
		cout << "num的类型是int类型" << endl;
	}

	return 0;
}
```

运行的结果为：

```cpp
num的类型是int类型
```

或者我们可以尝试一下指针：

```cpp
#include <iostream>
#include<typeinfo>
using namespace std;

int main() {

	auto num = 123;

	auto memoryAddress = &num;

	if (typeid(memoryAddress) == typeid(int*)) {
		cout << "memoryAddress是int指针类型" << endl;
	}

	return 0;
}
```

运行的结果为：

```cpp
memoryAddress是int指针类型
```

auto 仅仅是一个占位符，在编译器期间它会被真正的类型所替代。或者说，C++ 中的变量必须是有明确类型的，只是这个类型是由编译器自己推导出来的。