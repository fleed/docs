---
title: "Exceptions and Exception Handling (C# Programming Guide) | Microsoft Docs"

ms.date: "2015-07-20"
ms.prod: .net


ms.technology: 
  - "devlang-csharp"

ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exception handling [C#]"
  - "exceptions [C#]"
  - "C# language, exceptions"
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: 33
author: "BillWagner"
ms.author: "wiwagn"

translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Exceptions and Exception Handling (C# Programming Guide)
The C# language's exception handling features help you deal with any unexpected or exceptional situations that occur when a program is running. Exception handling uses the `try`, `catch`, and `finally` keywords to try actions that may not succeed, to handle failures when you decide that it is reasonable to do so, and to clean up resources afterward. Exceptions can be generated by the common language runtime (CLR), by the .NET Framework or any third-party libraries, or by application code. Exceptions are created by using the `throw` keyword.  
  
 In many cases, an exception may be thrown not by a method that your code has called directly, but by another method further down in the call stack. When this happens, the CLR will unwind the stack, looking for a method with a `catch` block for the specific exception type, and it will execute the first such `catch` block that if finds. If it finds no appropriate `catch` block anywhere in the call stack, it will terminate the process and display a message to the user.  
  
 In this example, a method tests for division by zero and catches the error. Without the exception handling, this program would terminate with a **DivideByZeroException was unhandled** error.  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## Exceptions Overview  
 Exceptions have the following properties:  
  
-   Exceptions are types that all ultimately derive from `System.Exception`.  
  
-   Use a `try` block around the statements that might throw exceptions.  
  
-   Once an exception occurs in the `try` block, the flow of control jumps to the first associated exception handler that is present anywhere in the call stack. In C#, the `catch` keyword is used to define an exception handler.  
  
-   If no exception handler for a given exception is present, the program stops executing with an error message.  
  
-   Do not catch an exception unless you can handle it and leave the application in a known state. If you catch `System.Exception`, rethrow it using the `throw` keyword at the end of the `catch` block.  
  
-   If a `catch` block defines an exception variable, you can use it to obtain more information about the type of exception that occurred.  
  
-   Exceptions can be explicitly generated by a program by using the `throw` keyword.  
  
-   Exception objects contain detailed information about the error, such as the state of the call stack and a text description of the error.  
  
-   Code in a `finally` block is executed even if an exception is thrown. Use a `finally` block to release resources, for example to close any streams or files that were opened in the `try` block.  
  
-   Managed exceptions in the .NET Framework are implemented on top of the Win32 structured exception handling mechanism. For more information, see [Structured Exception Handling (C/C++)](https://docs.microsoft.com/cpp/cpp/structured-exception-handling-c-cpp) and [A Crash Course on the Depths of Win32 Structured Exception Handling](http://go.microsoft.com/fwlink/?LinkId=119654).  
  
## Related Sections  
 See the following topics for more information about exceptions and exception handling:  
  
-   [Using Exceptions](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Exception Handling](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Creating and Throwing Exceptions](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Compiler-Generated Exceptions](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [How to: Handle an Exception Using try/catch (C# Programming Guide)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [How to: Execute Cleanup Code Using finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## C# Language Specification  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## See Also  
 <xref:System.SystemException>   
 [C# Programming Guide](../../../csharp/programming-guide/index.md)   
 [C# Keywords](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [Exceptions](http://msdn.microsoft.com/library/f99a1d29-a2a8-47af-9707-9909f9010735)   
 [Exception Hierarchy](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [Writing Reliable .NET Code](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [Minidumps for Specific Exceptions](http://go.microsoft.com/fwlink/?LinkId=112408)