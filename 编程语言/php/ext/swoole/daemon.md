# daemon

```m4
AC_CHECK_LIB(c, daemon, AC_DEFINE(HAVE_DAEMON, 1, [have daemon]))
```

```c
#ifndef HAVE_DAEMON
int daemon(int nochdir, int noclose)
{
    pid_t pid;

    if (!nochdir && chdir("/") != 0)
    {
        swWarn("chdir() failed. Error: %s[%d]", strerror(errno), errno);
        return -1;
    }

    if (!noclose)
    {
        int fd = open("/dev/null", O_RDWR);
        if (fd < 0)
        {
            swWarn("open() failed. Error: %s[%d]", strerror(errno), errno);
            return -1;
        }

        if (dup2(fd, 0) < 0 || dup2(fd, 1) < 0 || dup2(fd, 2) < 0)
        {
            close(fd);
            swWarn("dup2() failed. Error: %s[%d]", strerror(errno), errno);
            return -1;
        }

        close(fd);
    }

    pid = fork();
    if (pid < 0)
    {
        swWarn("fork() failed. Error: %s[%d]", strerror(errno), errno);
        return -1;
    }
    if (pid > 0)
    {
        _exit(0);
    }
    if (setsid() < 0)
    {
        swWarn("setsid() failed. Error: %s[%d]", strerror(errno), errno);
        return -1;
    }
    return 0;
}
#endif
```
