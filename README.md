# simple_log_project
最大化满足你需求的日志系统

### 需求

最大化满足需求的同时尽可能避免代码侵入



### 思路

通过AOP去切入你自定义的注解，不断维护你的注解类和切面类，最后将这个工具打包成jar包发布到maven仓库。

因为没有一款三方的插件可以完美覆盖你所有的需求，所以最好的方式就是按这个流程不断维护自己的工具。



### 介绍

1 导入文件：

```java
Log.java
LogAspect.java
```

前者定义注解

后者AOP切入注解，完善功能



2 在目标方法上添加

```java
@Log.MIDDLE(description = "标记测试方法")
public void aroundTest(String s) {
   // TODO..
}
```



3 执行结果

![result](https://yloopdaed-public.oss-cn-shanghai.aliyuncs.com/logaspect.jpg)

日记会记录使用的切面类型、执行的类和方法、传入参数、执行结果、持续时间等。



### 最后

你可以在 [JPP](https://github.com/YorickYu/JPP/tree/main/src/main/java/com/yy/annotation) 下载并使用这个小工具，谢谢