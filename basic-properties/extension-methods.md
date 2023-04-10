# extension methods

## static class

```c#
using System;
namespace extension_methods.extensionmethods
{
	public static class ExtensionMethodsForClass1
	{
		/// <summary>
		/// syntax for creating extension methods. use 'this' on first parameter which should be the og class where we want to add our extension method
		/// can only extend method to one class
		/// </summary>
		/// <param name="c1">adds method 'subtract' to class1</param>
		/// <param name="a"></param>
		/// <param name="b"></param>
		/// <returns></returns>

		public static int Subtract(this Class1 c1, int a, int b)
		{
			return a - b;
		}
	}
}
```

## receiving class

```c#
using System;
namespace extension_methods
{
	public class Class1
	{

		public string Name { get; set; }
		private int _age;
		protected int _height;

        // ^ private and protected fields are not going to be visible/usable in an extension method

        public int Sum(int a, int b) {
			return a + b;
		}


	}
}
```

## implementation

```c#
using System.Text;
using extension_methods;
using extension_methods.extensionmethods;

Class1 _class = new Class1();

Console.WriteLine(_class.Subtract(2, 4));

Console.ReadLine();

```
