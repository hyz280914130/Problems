## 通过Integer.toBinaryString() 方法，将一个十进制整数转换为一个二进制字符串

### 一、前述
<pre>
  toBinaryString()，是Integer包装类中的其中一个方法，类似的方法还有很多
</pre>

### 二、代码
```
public class HelloWorld {
   public static void main(String[] args) {
        int i = 5;
        String b = (Integer.toBinaryString(i)); // 5的二进制的表达101
        System.out.println(i+" 的二进制表达是: "+b);
    }
}
```
