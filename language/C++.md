# 1. 预备知识
## 1.1 面向对象OOP
- 封装（Encapsulation）：封装是将数据和方法组合在一起，对外部隐藏实现细节，只公开对外提供的接口。这样可以提高安全性、可靠性和灵活性。
- 继承（Inheritance）：继承是从已有类中派生出新类，新类具有已有类的属性和方法，并且可以扩展或修改这些属性和方法。这样可以提高代码的复用性和可扩展性。
- 多态（Polymorphism）：多态是指同一种操作作用于不同的对象，可以有不同的解释和实现。它可以通过接口或继承实现，可以提高代码的灵活性和可读性。
- 抽象（Abstraction）：抽象是从具体的实例中提取共同的特征，形成抽象类或接口，以便于代码的复用和扩展。抽象类和接口可以让程序员专注于高层次的设计和业务逻辑，而不必关注底层的实现细节。

## C++ compilation process
When you write a program in C++, your first step is to create a file that contains the text of the program, which is called a **sourcefile**. Before you can run your program, you need to translate the source file into an executable form. The first step in that process is to invoke a program called a **compiler**, which translates the source file into an objectfile containing the corresponding **machine-language instructions**. This object file is then combined with other object files to produce an **executablefile** that can be run on the system. The other object files typically include predefined object files called libraries that contain the machine-language instructions for various operations commonly required by programs. The process of combining all the individual object files into an executable file is called **linking**.
![[Pasted image 20240408193816.png]]



## 1.2 C++标准库
标准的 C++ 由三个重要部分组成：
1. 核心语言，提供了所有构件块，包括变量、数据类型和常量，等等。
2. C++ 标准库，提供了大量的函数，用于操作文件、字符串等。
3. 标准模板库（STL），提供了大量的方法，用于操作数据结构等。

## 1.3 C++注释Comments
- // - 一般用于单行注释。
    
- /* ... * /  - 一般用于多行注释。

## 1.4 数据类型
| 类型   | 关键字     | 位/字节 |
| ---- | ------- | ---- |
| 布尔型  | bool    |      |
| 字符型  | char    | 1    |
| 整型   | int     | 4    |
| 浮点型  | float   | 4    |
| 双浮点型 | double  | 8    |
| 无类型  | void    |      |
| 宽字符型 | wchar_t | 2or4 |
- 可以使用typedef声明一个新类型:
```
typedef type newname;
typedef int test;
test dis;
```

 - 枚举类型(enumeration)是C++中的一种派生数据类型，它是由用户定义的若干枚举常量的集合。
	 - 第一个名称的值为 0，第二个名称的值为 1，第三个名称的值为 2...
```
enum 枚举名{ 
     标识符[=整型常数], 
     标识符[=整型常数], 
... 
    标识符[=整型常数]
} 枚举变量;
```

### 1.4.1 类型转换 
类型转换：将一个数据类型的值转换为另一种数据类型的值，有以下四种转换：
- 静态转换（Static Cast）：将一种数据类型的值强制转换为另一种数据类型的值；
	- 静态转换不进行任何运行时类型检查，可能会报错；
```
int i = 10; 
float f = static_cast<float>(i);//int -> float
```
-  动态转换（Dynamic Cast）: 常用于将一个基类指针或引用转换为派生类指针或引用。动态转换在运行时进行类型检查，如果不能进行转换则返回空指针或引发异常
```
class Base {}; 
class Derived : public Base {}; 
Base* ptr_base = new Derived; 
Derived* ptr_derived = dynamic_cast<Derived*>(ptr_base); // 将基类指针转换为派生类指针
```

- 常量转换（Const Cast）:常量转换用于将 const 类型的对象转换为非 const 类型的对象；常量转换只能用于转换掉 const 属性，不能改变对象的类型。
```
const int i = 10; 
int& r = const_cast<int&>(i); // 常量转换，将const int转换为int
```
- 重新解释转换（Reinterpret Cast）: 重新解释转换将一个数据类型的值重新解释为另一个数据类型的值，通常用于在不同的数据类型之间进行转换。
```
int i = 10; 
float f = reinterpret_cast<float&>(i); // 重新解释将int类型转换为float类型
```


## 1.5 C++变量
- 变量：程序可操作的存储区的名称。
- 变量定义就是告诉编译器在何处创建变量的存储，以及如何创建变量的存储。

![[Pasted image 20240320195158.png]]
1. 整数类型（Integer Types）：
    
    - `int`：用于表示整数，通常占用4个字节。
    - `short`：用于表示短整数，通常占用2个字节。
    - `long`：用于表示长整数，通常占用4个字节。
    - `long long`：用于表示更长的整数，通常占用8个字节。
2. 浮点类型（Floating-Point Types）：
    
    - `float`：用于表示单精度浮点数，通常占用4个字节。
    - `double`：用于表示双精度浮点数，通常占用8个字节。
    - `long double`：用于表示更高精度的浮点数，占用字节数可以根据实现而变化。
3. 字符类型（Character Types）：
    
    - `char`：用于表示字符，通常占用1个字节。
    - `wchar_t`：用于表示宽字符，通常占用2或4个字节。
    - `char16_t`：用于表示16位Unicode字符，占用2个字节。
    - `char32_t`：用于表示32位Unicode字符，占用4个字节。
4. 布尔类型（Boolean Type）：
    
    - `bool`：用于表示布尔值，只能取`true`或`false`。
5. 枚举类型（Enumeration Types）：
    
    - `enum`：用于定义一组命名的整数常量。
6. 指针类型（Pointer Types）：
    
    - `type*`：用于表示指向类型为`type`的对象的指针。
7. 数组类型（Array Types）：
    
    - `type[]`或`type[size]`：用于表示具有相同类型的元素组成的数组。
8. 结构体类型（Structure Types）：
    
    - `struct`：用于定义包含多个不同类型成员的结构。
9. 类类型（Class Types）：
    
    - `class`：用于定义具有属性和方法的自定义类型。
10. 共用体类型（Union Types）：
    
    - `union`：用于定义一种特殊的数据类型，它可以在相同的内存位置存储不同的数据类型。

- 变量作用域：
	- 在函数或一个代码块内部声明的变量，称为**局部变量**。
	- 在函数参数的定义中声明的变量，称为**形式参数**。
	- 在所有函数外部声明的变量，称为**全局变量**。

- C++ 修饰符类型：
	- signed：表示变量可以存储负数。对于整型变量来说，signed 可以省略，因为整型变量默认为有符号类型。
	- unsigned：表示变量不能存储负数。对于整型变量来说，unsigned 可以将变量范围扩大一倍。
	- short：表示变量的范围比 int 更小。short int 可以缩写为 short。
	- long：表示变量的范围比 int 更大。long int 可以缩写为 long。
	- long long：表示变量的范围比 long 更大。C++11 中新增的数据类型修饰符。
	- float：表示单精度浮点数。
	- double：表示双精度浮点数。
	- bool：表示布尔类型，只有 true 和 false 两个值
	- char：表示字符类型。
	- wchar_t：表示宽字符类型，可以存储 Unicode 字符。

- C++ 中的类型限定符
	- const：const 定义常量，表示该变量的值不能被修改。 
	- volatile： volatile 告诉该变量的值可能会被**程序以外的因素改变**，如硬件或其他线程
	- restrict：restrict 修饰的指针是唯一一种访问它所指向的对象的方式。只有 C99 增加了新的类型限定符 restrict。 
	- mutable：表示类中的成员变量可以在 const 成员函数中被修改。 
	- static：用于定义静态变量，表示该变量的作用域仅限于当前文件或当前函数内，不会被其他文件或函数访问。
	- register：用于定义寄存器变量，表示该变量被频繁使用，可以存储在CPU的寄存器中，以提高程序的运行效率。

## 1.6 Lambda 函数与表达式
- 对匿名函数的支持,称为 Lambda 函数(也叫 Lambda 表达式)。
- Lambda 表达式把函数看作对象。Lambda 表达式可以像对象一样使用，比如可以将它们赋给变量和作为参数传递，还可以像函数一样对其求值。

## 1.7 C++ 字符串String

- Strings are mutable in C++
- You can add characters to Strings and Strings to Strings using **+= or +**
	- Strings must use double quotes"" and characters use single'' 
- You can use logical operator to compare the Strings

![[Pasted image 20240408214734.png]]
![[Pasted image 20240408214750.png]]

| 序号  | 函数 & 目的                                                                                                                                                  |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | **strcpy(s1, s2);**  <br>复制字符串 s2 到字符串 s1。                                                                                                               |
| 2   | **strcat(s1, s2);**  <br>连接字符串 s2 到字符串 s1 的末尾。连接字符串也可以用 + 号，例如:  <br><br>string str1 = "runoob";<br>string str2 = "google";<br>string str = str1 + str2; |
| 3   | **strlen(s1);**  <br>返回字符串 s1 的长度。                                                                                                                       |
| 4   | **strcmp(s1, s2);**  <br>如果 s1 和 s2 是相同的，则返回 0；如果 s1<s2 则返回值小于 0；如果 s1>s2 则返回值大于 0。                                                                      |
| 5   | **strchr(s1, ch);**  <br>返回一个指针，指向字符串 s1 中字符 ch 的第一次出现的位置。                                                                                               |
| 6   | **strstr(s1, s2);**  <br>返回一个指针，指向字符串 s1 中字符串 s2 的第一次出现的位置。                                                                                              |

### C String and C++ String
```c++
void myFunc(){
	String str = "hi" + "C++";//error, "hi" and "C++" is C Str
}
```

## 1.8 C++指针和引用
- &取地址符
- **指针**是一个变量，其值为另一个变量的地址，即，内存位置的直接地址。

- C++ 引用：引用变量是一个别名，是**某个已存在变量的另一个名字**。一旦把引用初始化为某个变量，就可以使用该引用名称或变量名称来指向变量。

- 引用与指针之间有三个主要的不同：
	- 不存在空引用。引用必须连接到一块合法的内存。一旦引用被初始化为一个对象，就不能被指向到另一个对象。
	- 指针可以在任何时候指向到另一个对象。
	- 引用必须在**创建时被初始化**。指针可以在任何时间被初始化

## 1.9 C++时间和日期
为了使用日期和时间相关的函数和结构，需要在 C++ 程序中引用 <ctime> 头文件


# 2. 面向对象编程

# 2. C++面向对象