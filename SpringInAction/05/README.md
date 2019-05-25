# 05 构建Spring Web应用程序 
>
## 05.1 Spring MVC起步
>
- Spring MVC基于模型-视图-控制器(Model-View-Controller,MVC)模式实现，能够帮你构建像Spring框架那样灵活和耦合的Web应用程序。
>
- Spring将请求在调度Servlet、处理器映射(handler mapping)、控制器以及视图解析器(view resolver)之间移动。
>
### 跟踪Spring MVC的请求
>
- 01 在请求离开浏览器时，会带有用户所请求内容的信息，至少会包含请求的URL，但是还可能带有其他的信息，例如用户提交的表单信息。
- 02 请求的第一站是Spring的DispatcherServlet。与大多数基于Java的Web框架一样，Spring MVC所有请求都会通过一个前端控制器(front controller)Servlet。前端控制器是常用的Web应用程序模式，在这里一个**单例的Servlet**将请求委托给应用程序的其他组件来执行实际的处理。在Spring MVC中，DispatcherServlet就是前端控制器。
- 03 DispatcherServlet的任务是将请求发送给Spring MVC控制器(controller)。控制器是一个用于处理请求的Spring组件。在典型的应用程序中可能会有多个控制器，DispatcherServlet需要知道应该将请求发送给哪个控制器。所以DispatcherServlet会查询一个或多个处理器映射(handler mapping)来确定请求的下一站在哪里。处理器映射会根据请求所携带的URL信息来进行决策。
- 04 一旦选择了合适的控制器，DispatcherServlet会将请求发送给选中的控制器。到了控制器，请求会卸下其负载(用户提交的信息)并耐心等待控制器处理这些信息。(实际上，设计良好的控制器本身只处理很少甚至不处理工作，而是将业务逻辑委托给一个或多个服务对象进行处理。)
- 05 控制器在完成逻辑处理后，通常会产生一些信息，这些信息需要返回给用户并在浏览器上显示。这些信息被称为模型(model)。不过仅仅给用户返回原始的信息是不够的——这些信息需要以用户友好的方式进行格式化，一般会是HTML。所以，信息需要发送给一个视图(view)，通常会是JSP。
- 06 控制器所做的最后一件事就是将模型数据打包，并且标示出用于渲染输出的视图名。它接下来会将请求连同模型和视图名发送回DispatcherServlet。
>
- 这样，控制器就不会与特定的视图相耦合，传递给DispatcherServlet的视图名并不直接表示某个特定的JSP。实际上，它甚至并不能确定视图就是JSP。相反，它仅仅传递了一个逻辑名称，这个名字将会用来查找产生结果的真正视图。DispatcherServlet将会使用视图解析器(view resolver)来将逻辑视图名匹配为一个特定的视图实现，它可能是也可能不是JSP。
>
- 既然DispatcherServlet已经知道由哪个视图渲染结果，那请求的任务基本上也就完成了。它的最后一站是视图的实现(可能是JSP)，在这里它交付给模型数据。请求的任务就完成了。视图将使用模型数据渲染输出，这个输出会通过响应对象传递给客户端(不会像听上去那样硬编码)。
>
### 搭建Spring MVC
>
#### 配置DispatcherServlet
>
- 传统的方式，配置在web.xml文件中，这个文件会放到应用的war包里面。
>
- DispatcherServlet配置在Servlet容器中。 
```
  ... extends AbstractAnnotationConfigDispatcherServletInitializer ...
```
>
### Spittr应用简介
>
- 构建一个简单的微博(microblogging)应用，实现在线社交的功能。
>
## 05.2 编写基本的控制器
>
```
  @Controller                               // 声明为一个处理器
  public class ClassNameController{
    
    @RequestMapping(value="/" ,method=GET)  // 处理对"/"的GET请求
    public String methodName(){
      return "String";                      // 视图名为 String
    }
    
  }
```
### 测试控制器
>
- mock测试 
>
### 定义类级别的请求处理
>
- 拆分@RequestMapping，并将其路径映射部分放到类级别上。
```
  @Controller                               
  @RequestMapping("/")                      // 将控制器映射到 "/"
  public class ClassNameController{
    
    @RequestMapping(method=GET)             // 处理对"/"的GET请求
    public String methodName(){
      return "String";                      // 视图名为 String
    }
    
  }
```
>
### 传递模型数据到视图中
>
- 
>
## 05.3 接受请求的输入
>
- Spring MVC允许以多种方式将客户端中的数据传送到控制器的处理器方法中，包括：
>
- 01 查询参数(Query Parameter)
- 02 表单参数(Form Parameter)
- 03 路径变量(Path Variable)
>
### 处理查询参数
>
- 
>
### 通过路径参数接受输入
>
- 
>
## 05.4 处理表单
>
### 编写处理表单的控制器
>
-
>
### 校验表单
>
-
>
## 05.5 小结
>
- 借助于注解，Spring MVC提供了近似于POJO的开发模式，这使得开发处理请求的控制器变得非常简单，同时也易于测试。
>
