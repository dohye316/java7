# java7
可变参数
可变参数
基本概念
java允许将同一个类中多个同名同功能但参数个数不同的方法，封装成一个方法。就可以通过可变参数实现
基本语法
访问修饰符 返回类型 方法名（数据类型...形参名）{
}
快速入门案例
看一个案例 类HspMethod，方法 sum {可以计算2个数的和，3个数的和，4.。5}
}

class VarParameter01{

	public static void main(String[] args) {
		HspMethod m = new HspMethod();
		System.out.println(m.sum(1,19,55,64,478,84,84,44,8,4));//10
		
	}
}
class HspMethod{
	public int sum(int n1, int n2){
		return n1 + n2;

	}
	public int sum(int n1, int n2, int n3){
		return n1 + n2 + n3;
	}
	public int sum(int n1, int n2, int n3, int n4){
		return n1 + n2 + n3 + n4;
	}
	//上面的三个方法名称相同，功能相同，参数个数不同--》使用可变参数优化
	//老韩解读
	//1.int...表示接收的是可变参数，类型是int，即可以接收多个int（0-多）
	//2.使用可变参数时，可以当做数组来使用，即nums可以当做数组
	public int sum(int ...nums){
		// System.out.println("接受的参数个数=" + nums.length);
		int res = 0;
		for (int i = 0; i < nums.length ;i++ ) {
               res += nums[i];		
		}
		return res;

	}
}

可变参数的注意事项和使用细节
1）可变参数的实参可以为0个或任意多个。
2）可变参数的实参可以为数组。
3）可变参数的本质就是数组
4）可变参数可以和普通类型的参数一起放在形参列表，但必须保证可变参数在最后
5）一个形参列表中只能出现一个可变参数



class VarParameter01{

	public static void main(String[] args) {
		int[]arr = {1,2,3};
		T t1 = new T();

	}
}
class T{
	public void pararmeter(int...nums){
         System.out.println("长度=" + nums.length);
		
	}
	public void f2(String str, double ...nums){
	// 不可以这样oublic void f2(double ...nums, String str)
		}
		不可以// public void f3(int...nums1,double...nums){

		// }
		// }


有三个方法，分别实现返回姓名和两门课成绩（总分），返回姓名和三门课成绩（总分）， 返回姓名和五门课成绩（总分）。 封装成一个可变参数的方法


class Varparameter01{
	public static void main(String[] args) {
		XiaoGuo hm = new XiaoGuo();
		

		System.out.println(hm.showScore("xiaoguo",25,46,55,88,88));
	}
}
class XiaoGuo{

	
	public String showScore(String name, int... score){
		int res = 0;
		for (int i = 0;i < score.length ;i++ ) {
                  res += score[i];			
		}   return name + score.length + "这门课的成绩总分为" + res;
	}
}

变量作用域
面向对象中，变量作用域是非常重要的知识点。
1.java编程中，主要的变量就是属性（成员变量）和局部变量。
2.我们说的局部变量一般是指在成员方法中定义的变量。
3.java中作用域的分类
全局变量：也就是属性，作用域为整个类体Cat类：cry eat等方法使用属性
局部变量：也就是除了属性之外的其他变量，作用域为定义它的代码块中！
4.全局变量可以不赋值，直接使用，因为有默认值，局部变量必须复制后，才能使用，因为没有默认值。

public class VarScope{
public static void main(String[] args) {
		
	}	
}
class Cat{
	//全局变量：也就是属性，作用域为整个类体Cat类：cry eat 等方法使用属性
	//属性在定义时，可以直接赋值
	int age = 10;//指定的值是10
	double weight;//默认为0.0

	public void cry(){//全局变量
		//1.局部变量一般是指在成员方法中定义的变量
		//2.n和name就是局部变量
		//3.n和name的作用域在cry方法中
        double weight;//默认是0.0
 
		int n = 10;
		String name ="jack";
		System.out.println("在cry中使用属性 age=" + age);
	}
	public void eat(){//局部变量
		System.out.println("在eat中使用 cry的变量 name =" + name);
	}
	public void hi(){
		int num;
		System.out.println("num=" + num);
		System.out.println("weight =" + weight);//没有赋值还是能输出
	}
}

作用域
注意事项和细节使用
1.属性和局部变量可以重名，访问时遵循就近原则。
2.在同一个作用域中，比如在同一个成员方法中，两个局部变量，不能重名。
2.在同一个作用域中，比如在同一个成员方法中，两个局部变量，不能重名。
3.属性生命周期较长，伴随着对象的创建而创建，伴随着对象的死亡而死亡。 局部变量，生命周期较短，伴随着它的代码块的执行而创建，伴随着代码块的结束而死亡。即在依次方法调用过程。
 
class VarScopeDetail{
	public static void main(String[] args) {
		Person p1 = new Person();
		p1.say();//当执行say方法时，say方法的局部变量比如name，会创建，当say执行完毕后
		//name局部变量就销毁，但是属性（全局变量）仍然可以使用
	}
}
class person{
	String name ="jack";
	public void say(){
		Stirng name = "king"//就近原则 King比较近name 出King
		String.out.println("say()name=" + name);
	}public void hi(){
		String address = "北京";
		String address = "上海";//报错不能重复address,重复定义变量
		String address = "hsp";//报错不能重复address,重复定义变量
	}
}

作用域注意事项和细节使用
作用域范围不同
全局变量：可以被本类使用，或其他类使用（通过对象调用）
局部变量：只能在本类中对应的方法中使用
修饰符不同
全局变量/属性可以加修饰符
局部变量不可以加修饰符

class VarScopeDetail{
	public static void main(String[] args) {
		Person p1 = new Person();
		p1.say();//当执行say方法时，say方法的局部变量比如name，会创建，当say执行完毕后
		//name局部变量就销毁，但是属性（全局变量）仍然可以使用
		T t = new T();
		t.test();//第一种跨类访问对象属性的方式
		t.test2(p1);//第二种跨类访问对象属性的方式
	}
}
class T{//全局变量/属性： 可以被本类使用，或其他类使用（通过对象调用）
	public void test(){
		Person p1 = new Person();
		System.out.println(p1.name);//输出jack
	
	}public void test2(Person p){
		
		System.out.println(p.name);//输出jack
	
	}
	
}
class person{
	private String name ="jack";//属性可以加private，public，proted等修饰符
	public void say(){
		// Stirng name = "king"//就近原则 King比较近name 出King
		String.out.println("say()name=" + name);
	}public void hi(){
		String address = "北京";//不可以加修饰符；private，public，proted
		String address = "上海";//报错不能重复address,重复定义变量
		String address = "hsp";//报错不能重复address,重复定义变量
	}
}

