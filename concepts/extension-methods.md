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

## entity class

```c#
using System;
using extension_methods_practice.extentionmethods.abstractions;

namespace extension_methods_practice.repo
{
	public class StudentEntity:IGetStudentToDTO
	{
		private string _firstName;
		private string _lastName;

		public void GetStudent(int id)
		{
            _firstName = "billy";
			_lastName = "bob";
        }

		public string GetFirstName()
		{
			return _firstName;
		}

        public string GetLastName()
        {
            return _lastName;
        }
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

### implementation

```c#
using extension_methods_practice.business;
using extension_methods_practice.extentionmethods.implementations;
using extension_methods_practice.repo;

StudentEntity _repoStudent = new StudentEntity();

_repoStudent.GetStudent(1);

StudentDTO _studentDTO1 = new StudentDTO();

_studentDTO1 = _repoStudent.MapToStudentDTONoInterface();

Console.WriteLine(_studentDTO1.StudentName);

Console.ReadLine();
```
