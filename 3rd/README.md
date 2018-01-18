# lodsve-3rd

> 顾名思义，这里是lodsve-framework所使用第三方jar包。因为一些原因，需要定制里面的一些文件，所以不适合用maven去管理，或者一些依赖根本就没有上传到maven repository中。使用的外部依赖有：

1. alibaba的fastdfs java client
2. sql日志工具p6spy

TODO：
后面将使用maven-shade-plugin对3rd包进行优化