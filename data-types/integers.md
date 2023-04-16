# integers

## try parse

```c#
using System;

public class Example
{
   public static void Main()
   {
      string[] values = { null, "160519", "9432.0", "16,667",
                          "   -322   ", "+4302", "(100);", "01FA" };
      foreach (var value in values)
      {
         int number;

         bool success = int.TryParse(value, out number);
         if (success)
         {
            Console.WriteLine($"Converted '{value}' to {number}.");
         }
         else
         {
            Console.WriteLine($"Attempted conversion of '{value ?? "<null>"}' failed.");
         }
      }
   }
}
// The example displays the following output:
//       Attempted conversion of '<null>' failed.
//       Converted '160519' to 160519.
//       Attempted conversion of '9432.0' failed.
//       Attempted conversion of '16,667' failed.
//       Converted '   -322   ' to -322.
//       Converted '+4302' to 4302.
//       Attempted conversion of '(100);' failed.
//       Attempted conversion of '01FA' failed.
```

- globalization options

```c#
using System;
using System.Globalization;

public class StringParsing
{
   public static void Main()
   {
      string numericString;
      NumberStyles styles;

      numericString = "106779";
      styles = NumberStyles.Integer;
      CallTryParse(numericString, styles);

      numericString = "-30677";
      styles = NumberStyles.None;
      CallTryParse(numericString, styles);

      styles = NumberStyles.AllowLeadingSign;
      CallTryParse(numericString, styles);

      numericString = "301677-";
      CallTryParse(numericString, styles);

      styles = styles | NumberStyles.AllowTrailingSign;
      CallTryParse(numericString, styles);

      numericString = "$10634";
      styles = NumberStyles.Integer;
      CallTryParse(numericString, styles);

      styles = NumberStyles.Integer | NumberStyles.AllowCurrencySymbol;
      CallTryParse(numericString, styles);

      numericString = "10345.00";
      styles = NumberStyles.Integer | NumberStyles.AllowDecimalPoint;
      CallTryParse(numericString, styles);

      numericString = "10345.72";
      styles = NumberStyles.Integer | NumberStyles.AllowDecimalPoint;
      CallTryParse(numericString, styles);

      numericString = "22,593";
      styles = NumberStyles.Integer | NumberStyles.AllowThousands;
      CallTryParse(numericString, styles);

      numericString = "12E-01";
      styles = NumberStyles.Integer | NumberStyles.AllowExponent;
      CallTryParse(numericString, styles);

      numericString = "12E03";
      CallTryParse(numericString, styles);

      numericString = "80c1";
      CallTryParse(numericString, NumberStyles.HexNumber);

      numericString = "0x80C1";
      CallTryParse(numericString, NumberStyles.HexNumber);
   }

   private static void CallTryParse(string stringToConvert, NumberStyles styles)
   {
      CultureInfo provider;

      // If currency symbol is allowed, use en-US culture.
      if ((styles & NumberStyles.AllowCurrencySymbol) > 0)
         provider = new CultureInfo("en-US");
      else
         provider = CultureInfo.InvariantCulture;

      bool success = int.TryParse(stringToConvert, styles,
                                   provider, out int number);
      if (success)
         Console.WriteLine($"Converted '{stringToConvert}' to {number}.");
      else
         Console.WriteLine($"Attempted conversion of '{stringToConvert}' failed.");
   }
}
// The example displays the following output to the console:
//       Converted '106779' to 106779.
//       Attempted conversion of '-30677' failed.
//       Converted '-30677' to -30677.
//       Attempted conversion of '301677-' failed.
//       Converted '301677-' to -301677.
//       Attempted conversion of '$10634' failed.
//       Converted '$10634' to 10634.
//       Converted '10345.00' to 10345.
//       Attempted conversion of '10345.72' failed.
//       Converted '22,593' to 22593.
//       Attempted conversion of '12E-01' failed.
//       Converted '12E03' to 12000.
//       Converted '80c1' to 32961.
//       Attempted conversion of '0x80C1' failed.
```
