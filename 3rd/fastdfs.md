# Alibaba FastDFS Java Client

> 定制化内容：

1. 格式化了一些代码
2. 增加了一个方法`com.alibaba.fastdfs.ClientGlobal#init(com.alibaba.common.FastDfsConfig config)`
3. 原来的代码，是只能读取给定的文件名，而我的配置文件加载方式，只能拿到`org.springframework.core.io.Resource`，然后包装成一个配置文件对象，后面会有介绍的
4. 所以对这个类进行了改造。
5. 原来的代码见[https://github.com/happyfish100/fastdfs-client-java](https://github.com/happyfish100/fastdfs-client-java "github")