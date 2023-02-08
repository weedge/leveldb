---
author: "weedge"
title: "源码阅读草稿-leveldb"
date: 2023-02-07T10:26:23+08:00
tags: [
	"leveldb",
]
categories: [
	"技术",
]
---

### 安装

leveldb源码使用tag 1.23, 在本地macOS 下通过vscode查看源码，编译debug如下：

```shell
git clone --recurse-submodules https://github.com/google/leveldb.git && cd leveldb && git checkout 1.23
brew install gflags
brew install snappy
mkdir -p build && cd build
cmake -DCMAKE_BUILD_TYPE=DEBUG .. && cmake --build .
cd ..
mkdir -p test && cd test
# touch test.cc edit code. 
# see https://github.com/google/leveldb/blob/main/doc/index.md 
# then compile build, don't use c++98 std, use c++11/c++14/c++17/c++a2 or more 
# know more ThreadSafetyAnalysis use by clang: https://clang.llvm.org/docs/ThreadSafetyAnalysis.html
# see more Macros documentation: https://gcc.gnu.org/onlinedocs/cpp/Macros.html (cpp: C preprocessor)
# tips: if use rust :)
clang++ -g -o test \
	test.cc ../build/libleveldb.a \
	-lpthread -lsnappy \
	-I../include/ \
	-std=c++17 \
	-O0 \
	-Wall
# use lldb to debug
# https://lldb.llvm.org/use/map.html
lldb test
```

单独checkout一个reviewcode分支用于源码查看注释理解后的代码：



### 整体代码框架



### 文件结构



### 写流程PUT

recover (WAL)



### 读流程GET

