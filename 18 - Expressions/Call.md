---
Source: https://leap.sei.org/help24/Expressions/Call.htm
---

# Call

## Syntax

Call(FunctionName, parameter1, parameter2, ...)  
or Call(FileName!FunctionName, parameter1, parameter2, ...)  
or Call(DLLFileName!DLLFunctionName, parameter1, parameter2, ...)

## Summary

Calls a function in an external script (e.g., VBScript of JavaScript) or DLL with any number of parameters.  The return value of the function or DLL is returned as the result of the expression.

## Calling Scripts

A script is a text file containing user-defined functions written in a scripting language, such as VB Script (.vbs), JScript (.js), Perl (.pl), Python (.py), PHP (.php) or Ruby (.rb).  VBScript and JScript come with Windows and are always available, whereas other scripting languages must be installed by you on your computer before you can use them in LEAP.

LEAP will look in the specified FileName for the function FunctionName.  If FileName is omitted, LEAP will look for a file called "functions.vbs" in the current area folder.  You can put commonly used functions into functions.vbs to make it easier to call them.  For example, as two trivial examples:

Function Add(x,y)  
Add = x + y  
End Function

Function Multiply(x,y)  
Multiply = x * y  
end Function

Notice that each function starts with the keyword Function and ends with the Keywords End Function. Function results are set by assigning values to the function name. LEAP functions should always return numeric values (integer or floating point) and should always use numeric parameters. Note though that it is possible to pass information about branch and variable IDs to scripts using functions such as [BranchID](BranchID.md), [VariableID](VariableID.md) and other similar functions. Functions can have any number of parameters, but the burden is on the user to pass the correct number of parameters in a comma separated list in the Call statement.

The following example expressions in could be used to call these two functions:

Call(Add, 5, 4)  
would return a value of 9

Call(Multiply, 5, 4)  
would return a value of 20

An error will be reported if the number or type of parameters are incorrect, or if you call a function that does not exist in the script file.  LEAP has its own built-in [script editor](../21.1%20-%20API/Using_the_Script_Editor.md) that can be used to edit, interactively debug and run scripts. You can edit the default functions.vbs file (located in the current area folder) using menu option [Advanced: Edit Functions](../21.1%20-%20API/Functions_Editor.md).

## Calling DLLs

A DLL is a Microsoft Windows "Dynamic Link Library" file that contains one or more functions. A DLL is a compiled executable program written in any standard programming language, such as C, Visual Basic or Delphi. The ability of LEAP to call DLL functions allows you to add new functions or even complete models to LEAP. The DLL function expects a parameter that is an array of double precision numbers, and should return one double precision number as the result.   Note: When LEAP, passes an array to a DLL, it automatically adds a parameter following the array which is the length of the array minus one (i.e. the index of the last element in the 0-based array).  For example, if the array has 5 elements, ArrayLengthMinusOne = 4.  Therefore, the C function must have two parameters: a pointer to a double array, and an integer which will be the array length minus one.

## Examples

Call( C:\DLLTest.dll!Sum, 1.5, -2.6, 3.0, 4.1, -4.2) ; will call a function called Sum in the DLL file c:\DLLTest.dll, passing it an array of 5 double precision numbers. (See C and Delphi source below)

Call( C:\DLLTest.dll ! Cos, month * 30) ; a Cosine wave, going from 30 degrees to 360 degrees over the year (See Delphi source below)

The parameters can include LEAP variables and function

## Sample C source code listing for test.c

Note: This can be compiled into Test.dll using a standard C compiler, such as the following free compilers: [Tiny C](http://bellard.org/tcc/), [Microsoft Visual Studio Express](https://www.visualstudio.com/en-us/products/visual-studio-express-vs.aspx), [MinGW](http://www.mingw.org/), [GNU GCC](http://gcc.gnu.org/), or [Orange C](http://www.members.tripod.com/~ladsoft/orange_c_compiler.html).

#include <windows.h>

#define DLLEXPORT __declspec(dllexport)

DLLEXPORT double Sum(double *Parameters, int ArrayLengthMinusOne);

DLLEXPORT double Sum(double *Parameters, int ArrayLengthMinusOne) {

 int i;  
double result;  
 result = 0;  
 for (i = 0; i <= ArrayLengthMinusOne; i++)  
   result += Parameters[i];  
return result;  
}

## Sample Pascal source code listing for test.dpr

Note: This can be compiled into Test.dll using the free [Lazarus Pascal Compiler](https://www.lazarus-ide.org/)

library DLLTest;  
  
{  
Simple Delphi program for testing calling DLLs from LEAP  
Call( C:\DLLTest.dll ! Sum, 1.5, -2.6, 3.0, 4.1, -4.2)  
Call( C:\DLLTest.dll ! Cos, month * 30)  
Call( C:\DLLTest.dll ! Sin, 90)  
}  
  
{$R *.res}  
  
// Sum up all the parameters  
function Sum(Parameters: array of double): double; stdcall;  
var  
i: integer;  
begin  
result := 0;  
  
for i := 0 to Length(Parameters) - 1 do  
  result := result + Parameters[i];  
end;  
  
const DegreeToRadianConversion = 2 * Pi / 360; // Convert from degrees to radians  
  
// Cosine of an angle expressed in degrees.  
function Cos(Parameters: array of double): double; stdcall;  
begin  
result := System.Cos(Parameters[0] * DegreeToRadianConversion);  
end;  
  
// Sine of an angle expressed in degrees.  
function Sin(Parameters: array of double): double; stdcall;  
begin  
result := System.Sin(Parameters[0] * DegreeToRadianConversion);  
end;  
  
// These are the functions that can be called by LEAP or other programs  
exports Sum, Cos, Sin;  
  
begin  
// nothing in the body  
end.