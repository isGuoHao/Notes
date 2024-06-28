# Driver Study

## 1. 遇到的问题

### 1.1 
1. 问题报错：

```bash
rmmod: ERROR: ../libkmod/libkmod.c:514 lookup_builtin_file() could not open builtin file '/lib/modules/6.9.0/modules.builtin.bin'
rmmod: ERROR: Module proc_test is not currently loaded
```
2. 问题原因：
    更新内核版本后，rootfs未同步更新，/lib/modules目录下缺少对应内核版本的目录以及modules.builtin.bin文件
3. 解决方法：
    (1) 根据报错，创建相应的目录
    (2) 拷贝内核编译产物中的modules.builtin和modules.order文件至新建目录
	(3) 执行命令 sudo depmod -a, 生成modules.builtin.bin
	(4) 再次加载、卸载驱动，可以看到不再出现报错
