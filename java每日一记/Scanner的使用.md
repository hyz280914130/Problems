## Scanner

### 一、什么是Scanner
<pre>
  Scanner可以从控制台获取输入的数据，然后进行处理。
</pre>

### 二、使用Scanner
```
import java.util.Scanner;

public class ScannerTest {

	public  static void main(String[] args) {
		
		Scanner s = new Scanner(System.in);
		System.out.println("请输入第一个整数");
		int a = s.nextInt();
		System.out.println("请输入第二个整数");
		int b = s.nextInt();
		System.out.println("请输入一个浮点数");
		float c = s.nextFloat();
		System.out.println("...");
		float i = a+b+c;
		System.out.println("计算结果为："+i);
		
	}
}

请输入第一个整数
1
请输入第二个整数
2
请输入一个浮点数
1.1
...
计算结果为：4.1
```

### 三、注意事项
<pre>
  在导入Scanner包的时候（java.util.Scanner）,类名不能使用Scanner，不然会冲突，导致无法导入Scanner。
<pre>
