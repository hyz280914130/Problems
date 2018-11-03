## this和super的使用

<pre>
  super代表父类实例本身
  super.xxx ：引用父类的成员变量
  super.yyy()：引用父类的成员方法
  super()：引用父类的构造函数
  
  this代表的是本类的实例本身
  this.xxx：引用本类的成员变量
  this.yyy()：引用本类的成员方法
  this():引用本类的构造函数
  this.class是获得这个类相对于Class类的对象
  
  * super()/this() 必须放在方法的第一行。
</pre>

## 在构造函数中使用this调用其他构造函数
```
public class Hero {
        
    String name; //姓名
        
    float hp; //血量
        
    float armor; //护甲
        
    int moveSpeed; //移动速度
        
    //带一个参数的构造方法
    public Hero(String name){
        System.out.println("一个参数的构造方法");
        this.name = name;
    }
      
    //带两个参数的构造方法
    public Hero(String name,float hp){
    	  this(name);
        System.out.println("两个参数的构造方法");
        this.hp = hp;
    }
 
    public static void main(String[] args) {
        Hero teemo =  new Hero("提莫",383);
         
        System.out.println(teemo.name);
         
    }
      
}
```
