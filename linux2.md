按“开发常用最小集合”整理：

---

# 一、`gcc`（编译）

## 1. 基本用法

```bash
gcc main.c -o main
```

## 2. 分步骤（重要）

```bash
gcc -E main.c   # 预处理
gcc -S main.c   # 生成汇编
gcc -c main.c   # 生成目标文件 .o
gcc main.o -o main  # 链接
```

## 3. 常用选项


```bash
gcc -g main.c -o main
```

```bash
gcc -O2 main.c
```

```bash
gcc -Wall -Wextra main.c
```

```bash
gcc -std=c11 main.c
gcc -std=c++17 main.cpp
```

```bash
gcc main.c -Iinclude -Llib -lmylib
```

```bash
gcc a.c b.c -o app
```

---

# 二、`make`（构建工具）


```sh
app: main.o util.o
	gcc main.o util.o -o app

main.o: main.c
	gcc -c main.c

util.o: util.c
	gcc -c util.c
```

## 2. 常用变量

```sh
CC = gcc
CFLAGS = -Wall -g

app: main.o
	$(CC) main.o -o app

main.o: main.c
	$(CC) $(CFLAGS) -c main.c
```

## 3. 自动变量（核心）

* `$@`：目标
* `$^`：所有依赖
* `$<`：第一个依赖

```make
app: main.o
	$(CC) $^ -o $@
```

## 4. 伪目标

```make
.PHONY: clean

clean:
	rm -f *.o app
```

## 5. 并行构建

```bash
make -j4
```

---

# 三、`strace`（系统调用追踪）

## 1. 基本用法

```bash
strace ./app
```

## 2. 常用场景

### 看程序做了什么系统调用

```bash
strace ls
```

### 跟踪文件操作

```bash
strace -e trace=open,read,write ./app
```

### 跟踪网络

```bash
strace -e trace=network ./app
```

### 跟踪某个进程

```bash
strace -p PID
```

### 输出到文件

```bash
strace -o log.txt ./app
```

## 3. 典型用途

* 调试“程序卡住”
* 找缺失文件（open失败）
* 分析IO/网络行为

---

# 四、`man`（文档系统）

## 1. 基本

```bash
man ls
man gcc
```

## 2. 指定章节（重要）

常见章节：

1. 用户命令
2. 系统调用
3. 库函数

```bash
man 2 open     # 系统调用
man 3 printf   # libc函数
```

## 3. 搜索

```bash
man -k printf     # 类似 apropos
man -f printf     # 简介
```

## 4. 在 man 内操作

* `/keyword`：搜索
* `n`：下一个
* `q`：退出

---

# 五、组合用法（开发常见）

## 1. 查函数定义

```bash
man 2 read
```

## 2. 调试程序行为

```bash
gcc -g main.c -o app
strace ./app
```

## 3. Make + 编译

```bash
make
make clean
```

