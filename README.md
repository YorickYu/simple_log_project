# simple_log_project
最大化满足你需求的日志系统

### 是什么

最大化满足需求的同时尽可能避免代码侵入

> 2020.12.3 更新
> 新增线程安全统计功能(基于ThreadLocal)
> 优化环绕切面中方法耗时统计


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
```
[main] INFO com.yy.annotation.LogAspect - START=======com.yy.annotation.TestAnnotation::hah777============
[main] INFO com.yy.annotation.LogAspect - DESC: asdfzxxzxzzxz
[main] INFO com.yy.annotation.LogAspect - ARGS: arg1=(string: aasdaf) arg2=(integer: 12) 
[main] INFO com.yy.annotation.LogAspect - ================================================================

[main] INFO com.yy.annotation.LogAspect - com.yy.annotation.TestAnnotation::resultfunc:1
[main] INFO com.yy.annotation.LogAspect - com.yy.annotation.TestAnnotation::hah777:3
```

此工具会记录使用的切面类型、执行类和方法、传入参数、执行结果、运行耗时等。

次工具会记录被标记的接口的调用次数，可以通过 `LogAspect.stat()` 输出。



### 最后

你可以在 [JPP](https://github.com/YorickYu/JPP/tree/main/src/main/java/com/yy/annotation) 或者当前这个项目中下载并使用这个小工具


