# class inheritance

## base class

```c#
using System;
namespace another_zork.classes
{
	// abstract means this class is a base class to be inherited by other more 'specific' classes
	public abstract class NPC
	{
		// protected fields can be acssesed by inheriting classes but not private ones

		protected int _power;

		public int Power { get { return _power; } set { _power = value; } }


		public void SetPower(int power)
		{
			Power = power;
		}

		public void HitWithSword()
		{
			Console.WriteLine("hit");
            Power -= 1;
		}

		public bool IsAlive()
		{
			if (_power>0)
			{
				return true;
			}
			return false;
		}

	}
}

```

## inheriting class

```c#
using System;
using another_zork.classes;

namespace another_zork.@base
{
	public class Witch: NPC
	{

	private bool _isFlying;

		public void IsFlying(bool isflying)
		{
			_isFlying = isflying;
		}

	public void HitWithSword()
	{
			if (!_isFlying)
			{
			Power -= 1;
				Console.WriteLine("hit");
			}
			Console.WriteLine("cant hit");

			_isFlying = !_isFlying;
	}

		public void HitWithArrow()
		{
			Power -= 1;
			Console.WriteLine("arrow hit");
		}

	}
}


```
