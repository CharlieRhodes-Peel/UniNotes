when you do:

	class_name  object_name = new class_name();
the class_name() is calling the constructor

How to define:

	class ClassName(){
		public ClassName (parameters){
			\\some elements
			\\ DO NOT RETURN ANYTHING
		}
	}
constructor name has to be same as class name
- looks like a method but is not
- but can use [[Overloading]]! 
looks as follows (example)

	public class Student{
		private int age;
		public Student(){
			age = 20;
		}	
		public Student(int a){
			age = a;
		}
	//rest of code
	}


