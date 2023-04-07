# dependency injection

## abstraction interface

```c#
using System;
namespace interfaces
{
	public interface ILogger
	{
		void Log(string message);
	}
}

```

## implementation class

```c#
using System;
namespace interfaces.implementations
{
	public class ConsoleLogger : ILogger
	{
        public void Log(string message)
        {
			Console.WriteLine(message);
		}
    }
}

```
