# 更新日志

## 2.7.5-RELEASE
1. 增加`lodsve-dependencies`来管理所有的依赖版本
2. 新增`lodsve-framework-bom`
3. 调整lodsve-amqp -> lodsve-rabbitmq
4. 新增lodsve-rocketmq

## 2.7.4-RELEASE
1. 升级solr和fastjson的版本
2. 清理未使用的依赖
3. 增加发布本地Maven私服

## 2.7.2-RELEASE(元旦特别纪念版)
1. 整理配置文件，并给每一个配置项添加注释
2. springfox移除获取path
3. 修改日志，将打印banner之前的日志全部去掉
4. 优化mybatis获取TypeHandler
5. 升级spring.data.mongodb 并修正一些问题
6. 解决relaxed bind绑定Map时的一个bug
7. flyway支持对多数据源数据库版本控制 fixed #30
8. 完善RelaxedBindFactory中的报错信息
9. 删除依赖commons-fileupload

## 2.7.1-RELEASE
1. 日志框架改为logback
2. 集成了travis
3. XXXProperties类的setter、getter方法都用Lombok的注解@Setter、@Getter实现
4. 使用aop来实现web每次请求打印参数及返回值
5. 美化readme，增加一些新的说明，修改链接
6. fixed bugs

## 2.7.0-RELEASE
1. 改进配置文件自动装配
    - map中的key用[]包裹起来
2. 重构mail部分，基于spring mail实现
3. 还原WeChat部分，并重构
4. 抽出rdbms部分（数据源相关）
5. 增加mybatis的通用dao、乐观锁插件
6. 升级相关组件
    - spring
    - junit 
    - jackson
    - springfox
    - commons-lang3
    - mybatis
    - 
7. 引入相关组件
    - vjtools    
    - guava
8. fixed bugs    

## 2.6.7-RELEASE
1. 支持amqp注解，具体配置请参考`rabbit.properties`文件
2. 使用EnableXXX的配置文件都从注解中引入，其余通过spring.factories引入
3. 修改validate加载错误文件的一个bug

## 2.6.6-RELEASE
1. 整理配置文件，对必填项加上@Required
2. 增加事务开关
3. p6spy改成profiles启用，优化mybatis加载数据源
4. 修改base64加解密的实现
5. 优化banner,可以在logger中打印
6. RelaxedBindFactory支持枚举类型
7. 获取json解析的工厂
8. 简化web.xml
9. 删除了wechat和workflow


## 2.6.5-RELEASE
1. 重构mybatis,取消自动生成beans
2. 整理mongodb
3. 多数据源配置连接池也是多个配置
4. 工具类重构、修改
    - 修改ObjectUtils相关
    - 将web相关utils移到lodsve-web中
    - 添加RestUtils
5. lodsve-web添加一层包路径web
6. params路径加载用WebApplicationInitializer实现
7. 优化验证码
    ```
    配置（server.properties）
    lodsve.server.enable-captcha=false
    lodsve.server.captcha-key=captchaKey
    lodsve.server.path=/captcha
    
    验证码图片路径  ${contextPath}/captcha
    校验验证码   lodsve.web.utils.CaptchaUtils.validate(request, code)
    ```

## 2.6.4.1-RELEASE
为软创开发 多数据源配置连接池也是多个配置

## 2.6.4-RELEASE
1. 多数据源支持多个数据库
2. @ConditionalOnProperty 可以使用RelaxedBind
3. 优化mybatis、druid的配置
4. 简化mongodb注解
5. fix bug

## 2.6.3-SNAPSHOT
1. 修改autoconfiguration-->relaxedbind
2. 修改PropertiesConfigurationFactory-->RelaxedBindFactory
3. 解决运行maven出现警告
4. 规范maven pom的写法
5. 添加copyright
6. 重构security
7. 3rd包使用shade插件去修改p6spy中的代码
8. 实现Ordered接口确保banner第一个被打印出来
9. 优化cache部分代码
10. 添加Windows下批处理文件

## 2.6.2-SNAPSHOT
1. 添加一些脚本
2. 添加webservice的支持
    - @EnableWebService
    - 必须在AppConfig中配置，不能再AppWebConfig中配置
    - 服务的bean的class上加上注解@WebService、@AddressProvider("/test").其中@AddressProvider不是必须的，如果不加这个注解，默认的路径为beanName
    - 其他配置在webservice.properties中配置
    - 修改lodsve-all使用的shade插件

## 2.6.1-RELEASE
修改maven-deploy时的一个问题，lodsve-all没有文件，生成javadoc会报错

## 2.6.0-RELEASE
修改GroupId，重新上传构建，并且定义新的发布规则及版本号
1. lodsve-3d: 无
2. lodsve-all: 新增所有子模块的聚合
3. lodsve-amqp: fixed bugs
4. lodsve-cache: 
    - 优化部分代码
    - 新增支持oscache、memcached
5. lodsve-core:
    - fixed bugs
    - 重构自动配置
    - 模仿spring-boot打印banner
    - 配置文件支持读取zookeeper
    - 整理优化一些代码
6. lodsve-dfs: 无
7. lodsve-mongodb: 无
8. lodsve-mybatis: 支持p6spy
9. lodsve-redis: 无
10. lodsve-search: 无
11. lodsve-security: 无
12. lodsve-test:
    - 支持embedded memcached、embedded redis
    - 使用@ParamsPath可以为单元测试注入配置文件路径
13. lodsve-validate: 无
14. lodsve-web:
    - fixed bugs
    - 禁用springfox时，不注册相关bean
15. lodsve-wechat: 无
16. lodsve-workflow: 无

## V2.5.10
1. ~~lodsve-dubbo~~: 删除
2. lodsve-mvc: 
    - 包名修改为lodsve-web
    - 解决对静态资源访问的问题
3. lodsve-springfox:
    - 参数简化
    - 显示网页标题及页面描述
4. lodsve-core：
    - 配置文件可以在开发环境中进行覆盖，详见 #1
    - 配置文件支持自动装配数组、List、Set、Properties、Class等类型，详见 #6
    - 资源文件类名修改
    - 更新condition
    - fix some bugs
5. lodsve-mybatis、lodsve-redis、lodsve-mongodb
    - 都支持多数据源，详见 #8
6. lodsve-cache:
    - 优化代码
7. lodsve-search:
    - 升级Lucene和solr到V6.6.0
    - 删除分词，可以在项目中配置

## V2.5.9
1. 根据ali-check对项目的一些代码进行合适的修改
2. 忽略spring-data中的spring版本
3. 修改lodsve-redis中包扫描路径
4. 升级mybatis版本
5. 删除dto convert
6. 添加mybatis性能监控、执行语句监控
7. 修改以前引入插件的一个bug、并且优化
8. 根据数据源自动加载主键自增长工具
9. 修改mysql自增长id生成工具
10. 删除支付
11. 增加一些线程共享变量
12. 优化lodsve-validate代码

## V2.5.8
1. 修改readme中的博客地址
2. 修改依赖的版本号
3. 运行main方法支持spring
4. 优化springfox的配置，springfox可以配置分组
5. 增加同步取主键
6. 重构配置文件加载
7. 重构autoconfigure，使@ConfigurationProperties可以在@Configuration配置文件中通过@Autowired使用
8. 修改license

## V2.5.7
1. 将配置文件的模板集成到框架中，目录为lodsve-core/resources/config-template
2. 添加maven发布自动close和release的插件
3. mybatis可以自定义拦截器
4. 是否是devMode的conditional
5. 常用的脚本语言在JVM中执行的相关封装
6. 修改关于conditional的webApplication的bug
7. 配置文件中，*.properties和framework/*.properties都加载到SystemConfig中
8. 修改config的目录结构
9. 增加lombok，后续使用
10. 移除dubbo基于注解的配置，使用xml的配置
11. 修改profile的配置

## V2.5.6
1. 前台传枚举的值或者code都支持反序列化

## V2.5.5
1. 修改pom,增加名为release的profile
2. 修复异常处理的bug
3. 升级flyway
4. 主键自增长
5. springfox配置描述信息
6. 系统配置文件路径结构修改
7. 重构validate

## V2.5.4
1. 修改dubbo版本
2. 框架的异常处理
3. 移除OSChina的maven配置,并修复一些依赖的问题

## V2.5.3
1. 实现spring-boot的condition,并修改框架中的一些实现
2. 修改包路径(改为lodsve)
3. 修改mybatis获取数据库类型的方式
4. 修改一些语法警告

## V2.5.2
1. 添加druid支持
2. 合并lodsve-base/lodsve-config/lodsve-logger为lodsve-core

## V2.5.1
1. 修改包路径为lodsve开头

## V2.4.11
1. 删除mybatis的通用repository，并修改相关联的代码
2. 配置: 增加必填项检查(@Required)
3. README.md添加logo

## V2.4.10
1. 完成简单工作流
2. swagger升级为springfox
3. 修改 cosmos-->lodsve
4. 支持spring cache
5. 修复若干bug

## V2.4.9
1. 修复父级pom忘记写入lodsve-logger了
2. mybatis不需要再写Enum的TypeHandler了,只需要在@EnableMyBatis中配置enumsLocations指定枚举在哪即可

## V2.4.8
1. 修改项目名为lodsve
2. 含义: Let our develop Spring very easy!
3. 修改相关文件夹名
4. 将groupId改成com.github.lodsve
5. 准备发布maven中央仓库相关工作

## V2.4.7
1. 将groupId改成com.github.cosmos

## V2.4.6
1. 调整项目结构
2. 添加微信公众号开发API
3. 简化security模块
4. 修改mybatis通用repository的CRUD返回值问题
5. 添加单元测试的(DBUnit Mockito PowerMockito Mock-Server)
6. 修改一些bug

## V2.4.5
1. mybatis支持排序

## V2.4.4
1. 新增dubbo支持
2. 通过配置spring的profile来控制是否启用swagger
3. 解决配置文件乱码问题
4. mybatis主键支持twitter的snowflake的ID生成器
5. 解决跨域问题
6. 修改一些bug

## V2.4.3
1. message-mybatis和message-mongodb配置basePackage时,默认是当前包路径
2. 解决之前spring-data-mongodb的版本冲突
3. swagger支持可配置路径

## V2.4.2
1. 使用Spring BeanWrapper实现配置即对象
2. servlet容器启动即加载properties和ini配置
3. 修改redis mongodb配置加载方式
4. mongodb mybatis等加载配置时,basePackage可以不写,默认是项目ApplicationConfiguration.java所在的包路径
5. domain自动转dto的一个bug修改
6. 关系型数据库使用类型安全的方式配置参数

## V2.4.1
1. 项目进行重构
2. 合并一些基础项目到message-base中
3. 重构spring的加载方式,eg:
    ```
    <!-- spring配置 start -->
    ...
    <servlet>
        <servlet-name>spring</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextClass</param-name>
            <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
        </init-param>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>...ApplicationConfiguration</param-value>
        </init-param>
    </servlet>
    ...
    <!-- spring配置 start -->
    
    ApplicationConfiguration.java
    @Configuration
    // ...
    @ComponentScan("your base packages")
    @ImportResource({"classpath*:/META-INF/springWeb/*.xml", "classpath*:/META-INF/spring/*.xml"})
    public class ApplicationConfiguration {
        // ...
    }
    ```

## V2.3.4
1. 添加message-mongodb,对mongodb的支持

## V2.3.3
1. 大量使用JavaConfig，抛弃原有的xml配置

## V2.3.2
1. 实现配置即对象

## V2.3.1
1. 删除message-jdbc
2. 修改message-security为mybatis实现
3. 将key和helper移到mybatis中

## V2.3
1. message-mybatis通用DAO完善

## V2.2.1
1. message-mybatis添加通用DAO

## V2.2
1. 封装了一些mybatis的操作 
2. 改进其他的一些功能

## V2.1
1. 重构message-jdbc 
2. 整理message-datasource(分为：关系型数据库、mongoldb、reds三种数据源...) 
3. restful返回json支持枚举(显示value和name) 
4. restful返回json格式化日期类型

## V2.0-GA
1. 模块拆分完成
    ```
    message-amqp
    message-base
    message-cache
    message-config
    message-datasource
    message-email
    message-event
    message-exception
    message-jdbc
    message-json
    message-logger
    message-mvc
    message-search
    message-security
    message-tags
    message-template
    message-test
    message-utils
    message-validate
    ```
2. 编写使用说明文档

## V1.0-GA
1. 整理代码,按模块分离
2. 初次提交