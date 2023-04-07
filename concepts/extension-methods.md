# extension methods

## abstraction interface

```c#
using System;
namespace extension_methods_practice.extentionmethods.abstractions
{
	public interface IGetStudentToDTO
	{
	}
}

```

## implementation class

```c#
using System;
using extension_methods_practice.business;
using extension_methods_practice.extentionmethods.abstractions;
using extension_methods_practice.repo;

namespace extension_methods_practice.extentionmethods.implementations
{
	public static class MapToStudentDTOWithInterface
	{
		public static StudentDTO MapToStudentDTOInterface(this IGetStudentToDTO obj, StudentEntity student)
		{
			StudentDTO studentToReturn = new StudentDTO();

			string name = $"{student.GetFirstName()} {student.GetLastName()}";

			studentToReturn.StudentName = name;
			return studentToReturn;
		}
	}
}

```
