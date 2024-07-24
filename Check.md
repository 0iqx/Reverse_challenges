# Check
One of the simplest challenges is a C# source code

```csharp
using  System;

  

public  class  check {
	public  static  void  Main(string[] args) {
	string  your_input  =  "";
	char[] array  =  your_input.ToCharArray();
	string[] array2  =  new  string[array.Length];
	string  enc  =  "";
	string  correct  =  "50887783103639797979785756352326260105";
	for (int  i  =  0; i  <  your_input.Length; i++) {
		array2[i] =  Convert.ToString((int)array[i] -  20);
		enc  +=  array2[i];
	}
	if (enc  ==  correct)
		Console.WriteLine("Good job!");
	else
		Console.WriteLine("Wrong Answer!");
	}
}
```
 1. Variable Initialization
	-   `your_input`: An empty string initialized here but meant to store the user's input.
	-   `array`: Converts `your_input` to a character array.
	-   `array2`: Initializes an array of strings with the same length as `array`.
	-   `enc`: An empty string meant to store the encoded result.
	-   `correct`: A pre-defined encoded string that the program will compare against.

 2. Encoding Loop
```csharp
for (int i = 0; i < your_input.Length; i++) {
    array2[i] = Convert.ToString((int)array[i] - 20);
    enc += array2[i];
}
```
-   The loop iterates over each character in `your_input`.
-   `(int)array[i] - 20` converts the character to its ASCII value and then subtracts 20.
-   `Convert.ToString` converts the resulting integer to a string.
-   The resulting string is stored in `array2[i]`.
- `enc` accumulates these string values.


**Encoding Logic:**

-   The encoding subtracts 20 from the ASCII value of each character. This is a straightforward but unusual encoding scheme.
-   The encoded string must match the hardcoded `correct` string for the output to be "Good job!".

so we can just inverse it i'll be using python:
We know that the flag format is Flag{...} so the `{` and `}` will be `123` and `105`.
```python
correct = "50 88 77 83 103 63 97 97 97 97 85 75 63 52 32 62 60 105"
for  char  in  correct.split():
	num  =  int(char) +  20
	print(chr(num), end="")
```
`Flag{Suuuui_SH4RP}`
