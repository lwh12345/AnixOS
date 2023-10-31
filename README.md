# AnixOS操作系统
![](./note/os.png)
![os](https://github.com/lwh12345/AnixOS/assets/89498547/3cec458f-3799-4f69-a808-3c351bca5731)

1. 加电

2. BIOS 自检 将主引导扇区读入 `0x7C00`

3. 进入主引导扇区 
   1. 清空屏幕
   
   2. 初始化段寄存器

   3. 读取 loader

   4. 跳转到 loader 执行

4. 进入 loader

   1. 检测内存
   
   2. 准备保护模式

      1. 打开 A20 线

      2. 加载 GDT
      3. 启动保护模式
      4. 跳转到保护模式
   3. 进入保护模式

   4. 加载段选择子
   5. 修改栈顶
   6. 读取内核
   7. 传入内存参数
   8. 跳转到内核执行

5. 初始化内核

    1. 进入内核 
    
    2. 初始化虚拟设备
    3. 初始化控制台
    4. 初始化全局描述符
    5. 加载选择子
    6. 初始化内存，得到内存大小
    7. 初始化内核：
       1. 初始化任务状态段
    
       2. 初始化物理内存管理数组
       3. 映射内核内存，启用分页机制
       4. 初始化内核堆内存管理
       5. 初始化中断
       6. 初始化时钟
       7. 初始化键盘
       8. 初始化时间
       9. 初始化实时时钟（目前没用到）
       10. 初始化串口
       11. 初始化 IDE 硬盘
       12. 初始化虚拟磁盘
       13. 初始化系统调用
       14. 初始化任务
       15. 初始化高速缓冲
       16. 初始化文件
       17. 初始化 inode
       18. 初始化超级块
       19. 开中断
    8.  初始化完成，等待时钟中断，进行调度
    9.  进入 init 内核线程
    10. 初始化设备
    11. 准备转入用户模式，执行 `/bin/init` 程序
    12. 执行 `/bin/osh` 程序，进入交互模式
