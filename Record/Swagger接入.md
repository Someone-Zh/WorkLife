# Swagger接入
------
## 简介
+ Swagger是一种接口描述语言，用于描述使用JSON表示的RESTful API。Swagger与一组开源软件工具一起使用，以设计，构建，记录和使用RESTful Web服务。Swagger包括自动文档，代码生成和测试用例生成。    --百科
+ 在开发初期文档和代码还可以保持一致性，但是多次迭代和更后就会出现代码和文档不一致问题，就要需要消耗资源去维护文档，并且api规范很难维持统一，为了解决这个问题去实现解决方案，当用的人多了就会成为一种规范，而swagger就是这样形成了，他不仅有很好的api规范，而且支持api的文档生成（Swagger UI），客户端代码生成（Swagger Codegen）、api页面编辑（Swagger Editor）、api调试（Swagger Inspector）。

## 实际接入
+ 接入采用swagger3.0 版本 为当前最新版，包含了老版本的功能和最新的api标准。
+ java的springboot项目直接引入官方start包即可一键配置
```xml
<dependency>
  <groupId>io.springfox</groupId>
  <artifactId>springfox-boot-starter</artifactId>
  <version>3.0.0</version>
</dependency>
```      
+ 代码配置详见https://springfox.github.io/springfox/docs/current/#springfox-spring-mvc-and-spring-boot
### swager运行流程
1. 由DocumentationPluginsBootstrapper（springfox.documentation.spring.web.plugins）启动开始，调用AbstractDocumentationPluginsBootstrapper#bootstrapDocumentationPlugins（）
2. 第一层级由顶层DocumentationPlugin开始遍历所有的文档，每个文档组件从springfox.documentation.spring.web.plugins.AbstractDocumentationPluginsBootstrapper#scanDocumentation扫描文档
3. 然后走向顺序执行下层遍历ApiListingScannerPlugin 去增强接口列表->OperationModelsProviderPlugin 增强操作模型 ->ApiModelReader 调用（ModelPropertyBuilderPlugin 和ModelBuilderPlugin） ->
4. ApiOperationReader-> 
  OperationBuilderPlugin列表：
  + ResponseBuilderPlugin由列表中的ResponseMessagesReader 调用
  + ParameterBuilderPlugin 由列表中的OperationParameterReader 调用（正常没问题如果要增强这部分会有小坑）
  + ResponseBuilderPlugin由列表中的ResponseMessagesReader调用
  + ExpandedParameterBuilderPlugin 由列表中OperationParameterReader
5. 结束有ApiListingScanner 最后调用ApiListingBuilderPlugin 
```
// springfox.documentation.spring.web.scanners.ApiDocumentationScanner#scan()
ApiListingReferenceScanResult result = apiListingReferenceScanner.scan(context);
    ApiListingScanningContext listingContext = new ApiListingScanningContext(context,
        result.getResourceGroupRequestMappings());
```
### 扩展功能
1. 目标
  目标是对每个api定义增加公司内部扩展定义，比如这个api属于哪个产品、哪个版本、安全隔离类型、访问控制组等信息。对api的入参和出参增强定义。
2. 准备
  swagger文档提供的单个api操作对象https://swagger.io/specification/v2/#operation-object中并不包括所需信息，所以将自定义信息保存到扩展之中。
  对单个api的操作需要自实现一个OperationBuilderPlugin来做对一个接口的增强。参数需要实现ParameterBuilderPlugin 来增强，实体模型（入参对象和返回对象）实现ModelPropertyBuilderPlugin来增强。
3. 问题（没有参数单独增强则不需要考虑）
  swagger对于没有Spring的四种注解（RequestBody、RequestPart、RequestParam、PathVariable）并且不是容器、枚举、map、swagger的ResolvedType类型默认自己去拆解对象生成信息，这样你自定义的参数增强就会失效，所以你还需要在实现一个OperationBuilderPlugin并且优先级在OperationParameterReader之后的去处理这个问题。
### Swagger小计
1. swagger的构建都是从上下文使用建造模式来构造最终对象。
2. 其他后续的其他插件重新设置则是覆盖并非更新。
