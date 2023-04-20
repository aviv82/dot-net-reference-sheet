# strings

## split

- split1

```c#
string s = "You win some. You lose some.";

string[] subs = s.Split(' ');

foreach (var sub in subs)
{
    Console.WriteLine($"Substring: {sub}");
}

// This example produces the following output:
//
// Substring: You
// Substring: win
// Substring: some.
// Substring: You
// Substring: lose
// Substring: some.
```

- split 2

```c#
string s = "You win some. You lose some.";

string[] subs = s.Split(' ', '.');

foreach (var sub in subs)
{
    Console.WriteLine($"Substring: {sub}");
}

// This example produces the following output:
//
// Substring: You
// Substring: win
// Substring: some
// Substring:
// Substring: You
// Substring: lose
// Substring: some
// Substring:
```

- split 3

```c#
string s = "You win some. You lose some.";
char[] separators = new char[] { ' ', '.' };

string[] subs = s.Split(separators, StringSplitOptions.RemoveEmptyEntries);

foreach (var sub in subs)
{
    Console.WriteLine($"Substring: {sub}");
}

// This example produces the following output:
//
// Substring: You
// Substring: win
// Substring: some
// Substring: You
// Substring: lose
// Substring: some
```

## substring

- substring 1

```c#
string [] info = { "Name: Felica Walker", "Title: Mz.",
                   "Age: 47", "Location: Paris", "Gender: F"};
int found = 0;

Console.WriteLine("The initial values in the array are:");
foreach (string s in info)
    Console.WriteLine(s);

Console.WriteLine("\nWe want to retrieve only the key information. That is:");
foreach (string s in info)
{
    found = s.IndexOf(": ");
    Console.WriteLine("   {0}", s.Substring(found + 2));
}

// The example displays the following output:
//       The initial values in the array are:
//       Name: Felica Walker
//       Title: Mz.
//       Age: 47
//       Location: Paris
//       Gender: F
//
//       We want to retrieve only the key information. That is:
//          Felica Walker
//          Mz.
//          47
//          Paris
//          F
```

- substring 2

```c#
String[] pairs = { "Color1=red", "Color2=green", "Color3=blue",
                 "Title=Code Repository" };
foreach (var pair in pairs)
{
    int position = pair.IndexOf("=");
    if (position < 0)
        continue;
    Console.WriteLine("Key: {0}, Value: '{1}'",
                   pair.Substring(0, position),
                   pair.Substring(position + 1));
}

// The example displays the following output:
//     Key: Color1, Value: 'red'
//     Key: Color2, Value: 'green'
//     Key: Color3, Value: 'blue'
//     Key: Title, Value: 'Code Repository'
```

## trim end

```c#
string sentence = "The dog had a bone, a ball, and other toys.";
char[] charsToTrim = {',', '.', ' '};
string[] words = sentence.Split();
foreach (string word in words)
   Console.WriteLine(word.TrimEnd(charsToTrim));

// The example displays the following output:
//       The
//       dog
//       had
//       a
//       bone
//       a
//       ball
//       and
//       other
//       toys
```
