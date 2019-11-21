---
title: try-except – příkaz
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: af378f510f11e1fe7d08619b5f33efe92a13d7be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245166"
---
# <a name="try-except-statement"></a>try-except – příkaz

**Microsoft Specific**

The **try-except** statement is a Microsoft extension to the C and C++ languages that supports structured exception handling.

## <a name="syntax"></a>Syntaxe

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// guarded code<br/>
> }<br/>
> **\_\_except** ( *expression* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// exception handler code<br/>
> }

## <a name="remarks"></a>Poznámky

The **try-except** statement is a Microsoft extension to the C and C++ languages that enables target applications to gain control when events that normally terminate program execution occur. Such events are called *exceptions*, and the mechanism that deals with exceptions is called *structured exception handling* (SEH).

For related information, see the [try-finally statement](../cpp/try-finally-statement.md).

Výjimky mohou být hardwarové nebo softwarové. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. For C++ programs, it is recommended that you use the C++ exception-handling mechanism ([try, catch, and throw](../cpp/try-throw-and-catch-statements-cpp.md) statements).

The compound statement after the **__try** clause is the body or guarded section. The compound statement after the **__except** clause is the exception handler. Obslužná rutina udává sadu akcí provedených v případě, že během provádění těla chráněné části dojde k vyvolání výjimky. Execution proceeds as follows:

1. Chráněná část je spuštěna.

1. If no exception occurs during execution of the guarded section, execution continues at the statement after the **__except** clause.

1. If an exception occurs during execution of the guarded section or in any routine the guarded section calls, the **__except** *expression* (called the *filter* expression) is evaluated and the value determines how the exception is handled. There are three possible values:

   - EXCEPTION_CONTINUE_EXECUTION (-1) Exception is dismissed. Program bude pokračovat tam, kde k výjimce došlo.

   - EXCEPTION_CONTINUE_SEARCH (0) Exception is not recognized. Continue to search up the stack for a handler, first for containing **try-except** statements, then for handlers with the next highest precedence.

   - EXCEPTION_EXECUTE_HANDLER (1) Exception is recognized. Transfer control to the exception handler by executing the **__except** compound statement, then continue execution after the **__except** block.

Because the **__except** expression is evaluated as a C expression, it is limited to a single value, the conditional-expression operator, or the comma operator. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

It is not valid to jump into a **__try** statement, but valid to jump out of one. The exception handler is not called if a process is terminated in the middle of executing a **try-except** statement.

For compatibility with previous versions, **_try**, **_except**, and **_leave** are synonyms for **__try**, **__except**, and **__leave** unless compiler option [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) is specified.

### <a name="the-__leave-keyword"></a>Klíčové slovo __leave

The **__leave** keyword is valid only within the guarded section of a **try-except** statement, and its effect is to jump to the end of the guarded section. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

A **goto** statement can also jump out of the guarded section, and it does not degrade performance as it does in a **try-finally** statement because stack unwinding does not occur. However, we recommend that you use the **__leave** keyword rather than a **goto** statement because you are less likely to make a programming mistake if the guarded section is large or complex.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Structured exception handling provides two intrinsic functions that are available to use with the **try-except** statement: `GetExceptionCode` and `GetExceptionInformation`.

`GetExceptionCode` returns the code (a 32-bit integer) of the exception.

The intrinsic function `GetExceptionInformation` returns a pointer to a structure containing additional information about the exception. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následující:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

The pointer types `PEXCEPTION_RECORD` and `PCONTEXT` are defined in the include file \<winnt.h>, and `_EXCEPTION_RECORD` and `_CONTEXT` are defined in the include file \<excpt.h>

You can use `GetExceptionCode` within the exception handler. However, you can use `GetExceptionInformation` only within the exception filter expression. Informace, na které ukazuje, jsou obecně umístěny do zásobníku a ve chvíli, kdy je řízení převedeno na obslužnou rutinu výjimky, jsou již nedostupné.

The intrinsic function `AbnormalTermination` is available within a termination handler. It returns 0 if the body of the **try-finally** statement terminates sequentially. Ve všech ostatních případech vrátí hodnotu 1.

excpt.h defines some alternate names for these intrinsics:

`GetExceptionCode` is equivalent to `_exception_code`

`GetExceptionInformation` is equivalent to `_exception_info`

`AbnormalTermination` is equivalent to `_abnormal_termination`

## <a name="example"></a>Příklad

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Výstup

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**END Microsoft Specific**

## <a name="see-also"></a>Viz také:

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
