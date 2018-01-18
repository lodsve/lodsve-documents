# lodsve-all

> 聚合了lodsve-framework的所有代码，方便没有使用maven的项目依赖

1. 正式版本，请到[Maven Release Repository](http://repo1.maven.org/maven2/com/lodsve/lodsve-all/ "Maven Release Repository")寻找
2. 快照版本，请到[Maven Snapshot Repository](https://oss.sonatype.org/content/repositories/snapshots/com/lodsve/lodsve-all/ "Maven Snapshot Repository")寻找


> 所遇到的坑点

1. 项目中有很多的`spring.facotries`文件，对这个文件不了解的，可以去找一下相关资料看看，类似于Java的ServiceLoader
2. 这个文件的格式如：

        org.springframework.context.annotation.Configuration=\
            lodsve.core.configuration.LodsveCoreConfiguration,\
            some other configuration
3. 我是用`maven-shade-plugin`进行合并的，起初，这些同名文件会被一个一个的覆盖掉，最终就剩下最后一个文件了
4. 后来在maven的官网上找到shade的使用办法，可以配置`transformer`来处理这些文件
5. 我使用了`ServicesResourceTransformer`处理Java的ServiceLoader文件`META-INF/services/...`
6. 发现依然不能处理我的问题，所以我就对这个插件进行了扩展
7. 新建了一个项目，名为`lodsve-maven-plugins`，代码可以在[Github](https://github.com/lodsve/lodsve-maven-plugins "Github")上查看。
8. 扩展了两个类
    1. `RegexAppendingTransformer`:匹配指定正则表达式的文件都进行合并
    2. `SpringFactoriesResourceTransformer`：单独对`spring.factories`文件进行合并