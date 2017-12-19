# gcc


## 编译时'pow未定义'
加上 -lm 参数链接数学库

似乎gcc除了标准库都不会自动链接，需要加 -l参数

[参考](https://www.zhihu.com/question/27416153/answer/78527688)
