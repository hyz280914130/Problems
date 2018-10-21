# Problems

### js中Function的几种写法
```
//第一种
function fun1(a,b){
  return a+b;
}

//第二种
//前面表示参数，后面表示函数语句，没有函数体
var fun2 = new function("a","b","return a+b");

//第三种匿名函数
var fun3 = function(a,b){
  return a+b;
}
```

### js中prop和attr的区别
```
  1.atto是通过搜索页面取值，必须在页面中明确定义才能搜索的到值，相对来说速度比较慢，例如
    <input name="test" type="checkbox">
    $("input:checkbox").attr("type"); 返回的是checkbox
    
  2.prop是从元素的属性中取值，即使有些属性没有明确定义，也能返回值，例如
    <input name="test" type="checkbox">
    $("input:checkbox").prop("checked");  返回true
    
  3.attr获取的是初始化值，除非通过attr(‘name’,’value’)改变，否则值不变。prop属性值是动态的，比如checkbox，选中后，checked变为true，prop值也会发生改变。
  
  4.自定义属性时使用attr，元素自带属性时使用prop
```

### get和post的区别
```
  1.get：
    get传递值时，将参数直接写在url的后面，安全性不高。
  2.post：
    post传递的值放在消息体中传递给后台，比get方式安全。
```

### doGet和doPost的区别
  本质上没有区别，都是经过service方法转向。只需将业务代码写在doPost方法体内，因为即便提交方法为doGet，在doGet方法体内也会调用doPost方法执行。

### JDK的环境变量配置和解释
[JDK的环境变量配置和解释](https://blog.csdn.net/root5/article/details/78024595)

### DBCP连接池和C3P0连接池的使用
[DBCP连接池和C3P0连接池的使用](https://blog.csdn.net/m15732622413/article/details/55193023)

### HTTP常见的状态码含义
    "200" : ok
    "302" : 重定向
    "400" : 错误请求
    "404" : 资源未找到
    "500" : 服务器内部错误

### web.xml中配置 / 和 /* 的区别
   / 和 /* 都可以匹配所有的请求资源，但其匹配的优先顺序是不同的。/在所有的匹配路径中，优先级最低，即当别的路径都无法匹配时，/所匹配的缺省Servlet才会进行相应的请求资源处理。而 /星号 匹配的优先级是高于/路径和星号.后缀的路径的（如星号.action,星号.jsp等路径）。
   [参考](https://blog.csdn.net/jinghuashuiyue2/article/details/78589655?locationNum=7&fps=1)
   
### request.getParameter和request.getAttribute的区别
  getParameter是接收从客户端传到服务器端的数据，而getAttribute是接收容器内的数据。
  
### bytes = new Byte[1024]缓冲器的原理
```
  byte[] bytes = new byte[1024];
  int n = 0;
  //把fis里的东西读取到bytes数组里
  while((n=fis.read(bytes))!=-1) 
  {
    //把字节转成String，从0到n变成String
    String w = String(bytes,0,n);
    Stytem.out.println(w);
  }
```
解释1024,fis执行read时，不会每读一个字节就对赋值，而是一直读，此时循环体因为判断语句而堵塞，无法进行循环，这种情况一直到读到n为1024大小时，数组读满了，然后释放堵塞，循环体得以执行，当循环体执行完毕后，fis又会根据上次读取的位置（上次读取1024个字节后会留下一个标记）继续读取，持续这个过程，直到没有可读取的数据时，程序返回-1代表读取完毕，循环条件不成立，输出w字符串的循环体也就不在执行了。

### request.setCharacterEncoding和response.setContentType
  request.setCharacterEncoding设置的是设置通过request取出的数据的编码，该方法必须执行在getParameter()方法之前，且只对post方法起作用。
  response.setContentType是设置页面的编码，response.setContentType("text/xml;charset=GBK")，前者设置动态文字（参数，数据库），后者设置后者设置页面静态文字，该方法必须在getWrite()或者response提交之前使用。
  使用response.setCharacterEncoding会覆盖response.setContentType的设置
  
### SimpleDateFormat使用
```
  // String --> Date
  String dateStr = "1996-06-07 00:00:00";
  SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss"); //日期格式可以该规定自己设置,比如可以不带时分秒
  Date date = format.parse(dateStr);
  
  // Date --> String
  Date date = new Date;
  SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss"); //日期格式可以该规定自己设置,比如可以不带时分秒
  Date dateStr = format.format(date);
```

### 四大作用域对象总结（request、session、application、pageContext）
一、request
  1.生命周期：访问时创建、响应结束销毁
  2.作用范围：一个请求链
二、session
  1.生命周期：服务器第一次执行request.getSession()时创建，不操作服务器30分钟后（可设置持久化，自定义时长），或者手动销毁（session.invalidate()）
  2.作用范围：整个会话期间
三、application
  1.相当于ServletContext
  2.生命周期：web应用被加载时创建（服务器启动），web应用被卸载时销毁（服务器关闭或移除该应用）
  3.作用范围：整个web应用
四、pageContext
  1.生命周期：当对jsp请求时创建，响应结束时销毁
  2.作用范围：整个jsp页面
  
### List、Set、Map
  1.List:可重复、有序
  2.Set：不可重复、无序
  3.Map:键不可重复、值可以重复
  
### 加载类的几种方式，加载类时包括类的加载过程
```
  //第一种
  Dog dog = new Dog();
  
  //第二种
  Class clazz = Class.forName("Dog");
  Object dog = clazz.newInstance();
  
  //第三种
  Class clazz = classLoader.loadClass("Dog");
  Object dog = clazz.newInstance();
  
  //第四种
  Object.clone(0
  
  //第五种 --- 反序列化
```

### 获得class对象的三种方式
  1.className.class
    这种方式不执行静态代码块和构造块
  2.Class.forName("类全名")
    这种方式执行静态代码块，但不执行构造块
  3.obj.getClass
    静态块和构造块一起执行
    
### 事务的四种隔离级别
  1.读未提交
    A更新了数据，但未提交，此时B查询数据，查询到的是A更新的数据，假如此时A回滚，相当于数据并未更新，但B却读取到了A之前更新的数据，也就是读到了脏数据。
  2.不可重复读
    A更新了操作，但未提交，此时B查询数据，查询到的是A未更新前的数据（因为不允许读未提交的数据），假如这个数据是400，然后A提交。另一边B又查询，因为这时A刚好提交，所以B查询到的是A更新并提交的数据，假如这个数据是450,与前一次查询的结果不一致，那么就导致了两次读取的数据不一致。
  3.可重复读
    A查询数据（假如数据为500），此时B更新数据并提交（-50操作），A在查询数据，结果一致（还是500），但A接着执行-50更新操作并提交，再次查询（结果为400）。这是因为在可重复读的机制下，select不会更新版本号，所以在B端的更新操作不会影响到A，但是insert、update和delete后更新版本号，这时候就会更新B端所进行操作后的数据了。
  4.串行化
    A在对数据库操作期间不允许其他客户端操作，只有等A操作完才能换B。这个方式效率极低。
    
### Hibernate中get()和load()的区别
  1.get()
    查询返回的是实际的对象，查询时立即发出sql语句。如果查询不到返回null,一般先查询一级缓存，然后二级缓存，最后查询数据库。
  2.load()
    查询返回的是代理对象，这个代理对象中只存储了目标对象的ID值，只有查询非ID属性时，才会发送sql语句。如果查询不到返回异常，因为一定返回代理对象，所以结果不为空，但访问代理对象代理的真正对象时，却发现并不存在，所以就抛出异常。
    
未完待续。。
    
  
