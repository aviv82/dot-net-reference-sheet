# datetime

- string to datetime verify/converter

```c#
public static DateTime StringToDate(string toConvert)
        {
            bool isValidDate = DateTime.TryParseExact(toConvert, "dd/MM/yyyy", CultureInfo.InvariantCulture, DateTimeStyles.None, out DateTime result);

            if (!isValidDate)
            {
                throw new Exception("invalid date or date format");
            }

            return result;

        }
```
