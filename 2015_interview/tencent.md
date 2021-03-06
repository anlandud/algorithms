## 腾讯面试 (2014/9/16)

### 一面

1 红黑树和平衡二叉树的区别

平衡二叉树(最严格的定义)：每个节点的左右子树的高度一样。

AVL树(较为宽松)：每个节点的左右子树的高度差的绝对值小于等于1。

红黑树(更为宽松)：每个节点的左右子树高度至多是两倍的关系。

2 为什么STL用的是红黑树

AVL树在每次修改时，都要对树进行平衡操作，代价比较高。而红黑树只需要在违背红黑树的规则时，才进行旋转，在查找效率与AVL树相当的情况下，修改的代价更低，因此，大多数应用都选择红黑树作为实现。

3 linux的进程内存映像

《深入理解计算机系统》上多次列出的那个内存映像图。

4 静态库和动态库

4.1 不考虑库

如果不考虑库时，当程序员调用printf时，就要将程序的目标文件与包含printf的目标文件进行链接，如果包含printf的目标文件中有许多其它的函数，不管程序员是否使用，都会链接到程序的目标文件构成可执行文件。

4.2 静态库

静态库可以理解为许多函数的目标文件的压缩包。当程序员调用printf时，只将printf的目标文件链接进来，不使用的函数不链接，因此，比不使用库的可执行文件的空间更小。

4.3 动态库

动态库主要的思想是共享。当程序员调用printf时，如果printf的目标代码已经在内存中，就可以直接使用该代码，而不需要在编译时将这部分代码链接进来。因此，编译这种程序时，编译器并不将printf的目标代码链接进来，而是在执行时，在内存中查找是否有printf的目标代码。这样的好处是，可执行文件比较小。

5 strcpy

主要考虑目标与源的地址范围可能重叠。

### 二面

1 什么是内存泄露吗？栈会发生内存泄露吗？如何避免内存泄露？

内存泄露就是new/malloc，但是没有delete/free，于是自己没有使用这部分内存，其它的进程也不能使用，就像内存“泄露”了一样。由于栈是自动管理的，因此，不存在内存泄露。

备注：去海豚浏览器面试时，面试官出了个关于new/delete和malloc/free的问题。

**面试官**：new的资源可以用free释放吗？

**我**：new的语义和delete的语义是对应的，new先分配内存，然后调用构造函数，delete先调用析构函数，然后释放内存，而malloc只分配内存，free只释放内存。因此，是不行的。

**面试官**：如果程序员就是要用free释放new的资源呢？

**我**：可能会出现运行时错误吧。(回来试了下，在codeblocks中，是可以的，没有出现任何问题)。

2 TCP中如果一端掉线，另一端知道吗？

3 如何查看TCP连接的状态？如果有过多的连接处于CLOSE_WAIT或者TIME_WAIT时会有什么问题？

4 解释纯虚函数(按照自己的理解)

当定义基类时，程序员要为这个基类添加一个方法，但是，这个方法对基类时没有意义的，或者说，程序员不知道该如何定义这个方法的函数体，这时就可以将这个方法声明为虚函数。

### 三面

1 简述项目，项目组有几个人？组员是如何沟通的？

2 一般从哪些途径了解互联网新闻？最近腾讯有什么新闻？

当时回答的是：百度新闻，微博。后来想想，是不是应该回答，腾讯新闻呢。。。

至于最近腾讯的新闻，还真是想不起来，最近都是阿里IPO的新闻，最后回答，微信的支付和滴滴打车。