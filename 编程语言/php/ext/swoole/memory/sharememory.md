## 共享内存

### 定义
```c
#define SW_SHM_MMAP_FILE_LEN  64

typedef struct _swShareMemory_mmap
{
    int size;
    char mapfile[SW_SHM_MMAP_FILE_LEN];
    int tmpfd;
    int key;
    int shmid;
    void *mem;
} swShareMemory;
```

sharememory 分别有基于sysv实现和基于mmap的实现,但只是使用了mmap的实现

### sysv实现
略
### mmap实现
略

### 内存结构

| swShareMemory | t_mem(真正返回的内存地址) |<br>
使用 sw_shm_malloc 返回的是共享内存首地址+swShareMemory占用大小的偏移量，calloc同理。

```c
void* sw_shm_malloc(size_t size)
{
    swShareMemory object;
    void *mem;
    //object对象需要保存在头部
    size += sizeof(swShareMemory);
    mem = swShareMemory_mmap_create(&object, size, NULL);
    if (mem == NULL)
    {
        return NULL;
    }
    else
    {
        memcpy(mem, &object, sizeof(swShareMemory));
        return mem + sizeof(swShareMemory); 
    }
}
```
