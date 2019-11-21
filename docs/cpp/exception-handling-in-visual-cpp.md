---
title: Exception handling in MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246595"
---
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

Výjimka je chybový stav, nacházející se případně i mimo řízení programu, který brání programu pokračovat dle jeho pravidelné cesty spuštění. Určité operace, včetně vytvoření objektu, vstupu a výstupu souboru a volání funkcí z jiných modulů, představují možné zdroje výjimek i v případě, že program pracuje správně. Robustní kód je na výjimky připraven a zpracovává je. To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   Ve většině aplikací jazyka C++ by mělo být použito zpracování výjimek jazyka C++, které je typově bezpečné a zajišťuje, že jsou v průběhu odvíjení zásobníku vyvolány destruktory objektu.

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   Systém Windows nabízí svůj vlastní mechanismus zpracování výjimek zvaný SEH. Jeho použití není vhodné pro programování v jazyce C++ ani při použití knihovny MFC. Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. Do not mix the error handling mechanisms; for example, do not use C++ exceptions with structured exception handling. Using C++ exception handling makes your code more portable, and it allows you to handle exceptions of any type. For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Postup vyhodnocení bloků catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nezpracované výjimky jazyka C++](unhandled-cpp-exceptions.md)

- [Kombinace výjimek v jazycích C (strukturované) a C++](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](cpp-language-reference.md)</br>
[x64 – zpracování výjimek](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
