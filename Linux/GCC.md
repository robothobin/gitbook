# GCC背后的故事

编译过程： 预处理、编译、汇编、链接

## 预处理

工作：

* 头文件包含

* 宏定义展开

* 条件编译等

gcc选项 -E 查看具体过程，对应工具为cpp

```
gcc -E helloworld.c
cpp -E helloworld.c
```



## 编译

工作：

* 语法检查(仅语法检查 -fsyntax-only)
  * 方便移植，可以选择遵循某个标准 -std=c99
* 编译器优化
  * -O2 优化登记2
  * -Os 代码最小优化
* 生成汇编语言文件

gcc选项 -S 查看具体过程，对应工具为cc

```
gcc -S helloworld.c
cc -S helloworld.c
```

生成helloworld.s

* helloworld.c

  ```
  #include <stdio.h>
  
  int main(void) {
      printf("hello world\r\n");
      return 0;
  }
  ```

* helloworld.s

  ```
  	.section	__TEXT,__text,regular,pure_instructions
  	.build_version macos, 10, 14
  	.globl	_main                   ## -- Begin function main
  	.p2align	4, 0x90
  _main:                                  ## @main
  	.cfi_startproc
  ## %bb.0:
  	pushq	%rbp
  	.cfi_def_cfa_offset 16
  	.cfi_offset %rbp, -16
  	movq	%rsp, %rbp
  	.cfi_def_cfa_register %rbp
  	subq	$16, %rsp
  	leaq	L_.str(%rip), %rdi
  	movl	$0, -4(%rbp)
  	movb	$0, %al
  	callq	_printf
  	xorl	%ecx, %ecx
  	movl	%eax, -8(%rbp)          ## 4-byte Spill
  	movl	%ecx, %eax
  	addq	$16, %rsp
  	popq	%rbp
  	retq
  	.cfi_endproc
                                          ## -- End function
  	.section	__TEXT,__cstring,cstring_literals
  L_.str:                                 ## @.str
  	.asciz	"hello world\r\n"
  
  
  .subsections_via_symbols
  ```

  

  ## 汇编

  工作：

  * 将汇编代码翻译成目标代码（机器代码），但还不能直接运行

  gcc选项 -c 查看具体过程，对应工具为as
  
  ```
  gcc -c helloworld.s
as -c helloworld.s
  ```
  
  ```
  file helloworld.o
helloworld.o: Mach-O 64-bit object x86_64
  ```

  

  
  
  

