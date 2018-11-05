## 什么是枚举类型
> 枚举类型是一种特殊的类，在类中可以很方便的定义常量，常和switch语句搭配进行判断

### 代码
```
//定义英雄的分类
public enum Hero {
  //TANK (坦克)
  //WIZARD (法师 )
  //ASSASSIN (刺客)
  //ASSIST (辅助)
  //WARRIOR (近战)
  //RANGED (远程)
  //PUSH (推进)
  //FARMING (打野)
	TANK,WIZARD,ASSASSIN,ASSIST,WARRIOR,RANGED,PUSH,FARMING
}
```

### switch
> 提示：swicth支持 byte、short、int、char、String、enum六种类型判断。
```
public class Test{

  Hero ranged = Hero.RANGED
  
  switch(ranged){
    case TANK: 
      System.out.println("我是坦克，前排抗伤害");
      break;
    case WIZARD: 
      System.out.println("我是法师，后排输出和控制");
      break;
    case ASSASSIN： 
      System.out.println("我是刺客，爆炸输出秒掉C位");
      break;
    case WARRIOP：
      System.out.println("我是近战，前排输出")；
      break;
    case RANGEN:
      System.out.println("我是远程，后排输出")；
      break;
    case PUSH：
      System.out.println("我是推进，负责带线");
      break;
    case FARMING:
      System.out.println("我是打野，游走抓人");
      break;
  }
}
```
