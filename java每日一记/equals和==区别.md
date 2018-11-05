## 说明
> 1.equals() ： 是object方法，用于判断两个对象的内容是否相同，假设，当两个英雄的hp相同的时候，我们就认为这两个英雄相同

> 2."==" ： 不是Object的方法，用于判断两个对象是否相同，更准确的讲，用于判断两个引用，是否指向了同一个对象

## 代码
```
public class Hero {
    public String name; 
    protected float hp;
     
    public boolean equals(Object o){
    	if(o instanceof Hero){
    		Hero h = (Hero) o;
    		return this.hp == h.hp;
    	}
    	return false;
    }
     
    public static void main(String[] args) {
    	Hero h1= new Hero();
    	h1.hp = 300;
    	Hero h2= new Hero();
    	h2.hp = 400;
    	Hero h3= new Hero();
    	h3.hp = 300;
    	
    	System.out.println(h1.equals(h2)); //false
    	System.out.println(h1.equals(h3)); //true
      
        System.out.println(h1==h2); //false
    }
}

```
