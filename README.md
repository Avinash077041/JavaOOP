# JavaOOP
//1.......Singleton class,final and enum keyword.@@@@

 class A{
	private static A a=null;
	private A() {
		System.out.println("I am from default constructor");
	}
	static A getRef() {
		if(a==null) {
			 a=new A();           //1st way of creating object
		}return a;
	}
}
class Avi{
	public static void main(String[] args)throws Exception {
		A s1=A.getRef();
		A s2=A.getRef();
		System.out.println(s1);
		System.out.println(s2);		
	}
}

//2......Second way of creating object  

class A{
	 static A a=new A();     //2st way of creating object at loading time
//	static  {
//		a=new A();               //3st way of creating object
//	}
//	private A() {
//		System.out.println("I am from default constructor");
//	}
	static A getRef() {
		return a;
	}
	void m1() {
		System.out.println("m1");
	}
}
class Avi{
	public static void main(String[] args)throws Exception {
		A s1=A.getRef();
		A s2=A.getRef();
		System.out.println(s1);
		System.out.println(s2);
		s2.m1();                     //accessing instance method without creating object in main()
	}
}

//3.....Early instantiation in singleton classes
class A{
	private static A obj=new A();
	private A() {
		System.out.println("I am from no arg constructor");
	}
	static A getRef(){
		return obj;
	}
	void m1(){
		System.out.println("I am from m1 method");
	}
}
class Avi{
	public static void main(String args[])throws Exception {
		A s1=A.getRef();
		s1.m1();
		A s2=A.getRef();
		A s3=A.getRef();
		if(s1==s2 && s2==s3) {
			System.out.println("Three object pointing to the same reference id in heap memory");
		}
		else {
			System.out.println("Every object is not pointing to the same reference id in heap memory");
		}
	}
}

//4.....Lazy instantiation in singleton classes

class A{
	private static A obj=null;
	 private A() {
		System.out.println("I am from no arg constructor");
	}
	 static A getRef(){ 
		 if(obj==null) {
			  obj=new A();
		 }
			 return obj; 
	} 
	void m1(){
		System.out.println("I am from m1 method");
	}
}
class Avi{
	public static void main(String args[]) {
		A s1=A.getRef();
		s1.m1();
		A s2=A.getRef();
		A s3=A.getRef();
		if(s1==s2 && s2==s3) {
			System.out.println("Three object pointing to the same reference id in heap memory");
		}
		else {
			System.out.println("Ever object is not pointing to the same reference id in heap memory");
		}
	}
}




