---
tags:
  - csharp
---
# Working with Strings

* `\` can be used to escape sequences into literal strings
* `\n` can be used to create a new line
* `\\` can be used to use an actual \ within the string, escaping it immediately
* `@` in front of the string ensures C# understands we want to use the \\ characters
* `{0}` can be used as replacement code to be replaced by a value at the end of the string
* `{O:C}` will be replaced with a currency value
* `{0:N}` will add in decimal points and commas to show a number in an easier to read format
* `{0:P}` will show the value as a percentage
* Custom formats can also be used such as `{0: (###) ###-####}` as an example for an American phone number

```c#
            // string myString = "My \"so-called\" life ";
            // string myString = "What if I need a\n new line?";
            // string myString = "Go to your C:\\ drive";
            // string myString = @"Go to your C:\ drive";
            // string myString = String.Format("{0} = {0}", "First", "Second");
            // string myString = string.Format("{0:C}", 123.45);
            // string myString = string.Format("{0:N}", 12312313123123);
            // string myString = string.Format("{0:P}", .123);
            // string myString = string.Format("Phone Number: {0:(###) ###-####}", 1234567899);
```

* `myString.Substring




