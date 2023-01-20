# 实验二BUG记录

## BUG1

fatal error: generated/autoconf.h: 没有那个文件或目录 #include <generated/autoconf.h>

产生原因：为了给实验一截图，不得不重新执行下列指令，导致generated/autoconf.h库被清除

```text
make mrproper
make menuconfig
```

解决方法：重新编译内核

## BUG2

