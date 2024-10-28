# 0. XV6
 - CTRL a + c

# 1. 基础
Command-Line Arguments：命令行参数
```
void main(int argc,char** argv)
给main函数传递两个参数，argc和argv。
 - argc是int类型的，它表示的是命令行参数的个数。不许要用户传递，它会根据用户从命令行输入的参数个数，自动确定。
 - argv是char**类型的，它的作用是存储用户从命令行传递进来的参数。它的第一个成员是用户运行的程序名字。
```
