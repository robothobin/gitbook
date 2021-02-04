# ELF文件

Executable and Linkable Format

一种用于二进制文件、可执行文件、目标代码、共享库和核心转储格式文件

组成：

* ELF header
* Program header table
* Section header table
* Section

## case

```
/* myprintf.c */
#include <stdio.h>
void myprintf(void)
{
    printf("hello, world!n");
}
```

```
/* test.h -- myprintf function declaration */
#ifndef _TEST_H_
#define _TEST_H_
void myprintf(void);
#endif
```

```
/* test.c */
#include "test.h"
int main()
{
    myprintf();
    return 0;
}
```



## ELF header

描述文件类型、程序入口等信息

REL    (Relocatable file)

EXEC (Executable file)

## Program header table

## Section header table

## Section

.rodata 只读数据，如hello world

.data 包含初始化的数据

.bss 包含未初始化的数据





