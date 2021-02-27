---
title: JVM log
date: 2021-02-27 15:48:49
tags:
---

## JVM 常用参数
### 当java应用内存溢出是保存内存映像，之后用MAT分析
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=directory
### 设置gc日志文件的目录
-Xloggc:${目录}/gc.log

## JVM常用命令
