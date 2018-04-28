---
title: libxml2的hash算法
categories: 
- c
- libxml2
tags:
- libxml2
layout: post
---

```c
unsigned long has_code(char* name){
  unsigned long value = 0L;

  if (name != NULL) {
	while (*name) {
	    value = value ^ ((value << 5) + (value >> 3)) + *name++;
	}
  }

  return value;
}

```
