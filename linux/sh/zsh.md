# zsh

## oh my zsh

### windows下配置oh-my-zsh卡顿(cygwin,msys2,babun等...)
主要是在theme中搜集git信息是耗费的时间较多

尝试隐藏git是否更改的信息
```gitconfig
[oh-my-zsh]
  hide-dirty=1
```

注释一些暂时不清楚的代码
```shell
zstyle ...
```

去掉一些内置的插件

换个theme居然解决了，起码卡顿不明显...

尝试优化收集git信息的shell TODO
