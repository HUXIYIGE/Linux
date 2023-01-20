# Linux实验三BUG记录

## BUG1

开始时，理解有一些问题，只是敲入参考代码，在实验二的基础上，进行一些修改。编译时，发现爆出很多未定义错误。

### 产生原因

参考代码中的涉及的数据结构对应的头文件没有引用，比如blkdev.h和blk_types.h。

### 解决方法

根据报错提示信息，在网上搜寻每一个数据结构所在的头文件，然后添加在darkelf.c文件中

## BUG2

在实验所给的参考代码中，有一个elf_queue_bio的变量，在引用头文件之后，仍然会报错elf_queue_bio未定义

### 产生原因

因为参考代码中并未给出定义，实际上elf_queue_bio其实是需要绑定的制造请求函数，函数原型如下：

```c
void (make_request_fn) (struct request_queue *q, struct bio *bio)
```

### 解决方法

虽然本次实验不需要细化这个函数，但是我们仍需要给出基本的函数定义，然后作为参数传递给blk_queue_make_request函数，才能完成实验