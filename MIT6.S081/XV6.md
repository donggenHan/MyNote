# 0. XV6
 - 退出：CTRL a + x
 - 编译：make qemu
 - 测试：./grade-lab-util sleep
 - 评分：make grade

# # C language
Command-Line Arguments：命令行参数

- argc 是argument count的缩写表示传入main函数中的参数个数，包括这个程序本身
- argv 是 argument vector的缩写表示传入main函数中的[参数列表](https://zhida.zhihu.com/search?content_id=147646623&content_type=Article&match_order=1&q=%E5%8F%82%E6%95%B0%E5%88%97%E8%A1%A8&zhida_source=entity)，其中argv[0]表示这个程序的名字
```
void main(int argc,char** argv)
给main函数传递两个参数，argc和argv。
 - argc是int类型的，它表示的是命令行参数的个数。不许要用户传递，它会根据用户从命令行输入的参数个数，自动确定。
 - argv是char**类型的，它的作用是存储用户从命令行传递进来的参数。它的第一个成员是用户运行的程序名字。
```

# Lab1:Utilities