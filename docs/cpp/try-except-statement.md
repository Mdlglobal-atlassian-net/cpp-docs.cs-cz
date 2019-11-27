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

**Specifické pro společnost Microsoft**

Příkaz **try-except** je rozšířením společnosti Microsoft pro jazyky C a C++ , které podporuje strukturované zpracování výjimek.

## <a name="syntax"></a>Syntaxe

> **vyzkoušení \_\_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//chráněný kód<br/>
> }<br/>
> **\_\_s výjimkou** ( *výraz* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;kód obslužné rutiny výjimky &nbsp;//<br/>
> }

## <a name="remarks"></a>Poznámky

Příkaz **try-except** je rozšířením společnosti Microsoft pro jazyky C a C++ , které umožňuje cílovým aplikacím získat kontrolu nad tím, kdy dochází k událostem, které obvykle ukončí provádění programu. Tyto události se nazývají *výjimky*a mechanismus, který se zabývá výjimkami, se nazývá *strukturované zpracování výjimek* (SEH).

Související informace naleznete v [příkazu try-finally](../cpp/try-finally-statement.md).

Výjimky mohou být hardwarové nebo softwarové. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro C++ programy se doporučuje použít mechanismus zpracování C++ výjimek (příkazy[Try, Catch a throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

Složený příkaz za klauzulí **__try** je tělo nebo chráněný oddíl. Složený příkaz za klauzulí **__except** je obslužná rutina výjimky. Obslužná rutina udává sadu akcí provedených v případě, že během provádění těla chráněné části dojde k vyvolání výjimky. Provádění pokračuje následujícím způsobem:

1. Chráněná část je spuštěna.

1. Pokud během provádění chráněné části nedojde k žádné výjimce, vykonání pokračuje v příkazu za klauzulí **__except** .

1. Pokud dojde k výjimce při provádění chráněného oddílu nebo v jakékoli rutině chráněného oddílu, je vyhodnocen *výraz* __except (nazývaný výraz *filtru* ) a hodnota určuje, jak je výjimka zpracována. Existují tři možné hodnoty:

   - Výjimka EXCEPTION_CONTINUE_EXECUTION (-1) byla zrušena. Program bude pokračovat tam, kde k výjimce došlo.

   - Výjimka EXCEPTION_CONTINUE_SEARCH (0) nebyla rozpoznána. Pokračujte v hledání zásobníku pro obslužnou rutinu, nejprve pro příkazy **try-except** a potom pro obslužné rutiny s další nejvyšší prioritou.

   - Je rozpoznaná výjimka EXCEPTION_EXECUTE_HANDLER (1). Převeďte řízení na obslužnou rutinu výjimky spuštěním složeného příkazu **__except** a potom pokračujte v provádění po bloku **__except** .

Vzhledem k tomu, že výraz **__except** je vyhodnocen jako výraz jazyka C, je omezen na jedinou hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

Skok na příkaz **__try** není platný, ale je platný pro skok mimo jeden. Obslužná rutina výjimky není volána, pokud je proces ukončen uprostřed provádění příkazu **try-except** .

Z důvodu kompatibility s předchozími verzemi jsou **_try**, **_except**a **_leave** synonyma pro **__try**, **__except**a **__leave** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

### <a name="the-__leave-keyword"></a>Klíčové slovo __leave

Klíčové slovo **__leave** je platné pouze v rámci chráněné části příkazu **try-except** a jeho efekt je přejít na konec chráněné části. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

Příkaz **goto** může také přejít mimo chráněný oddíl a nesnižuje výkon, protože je v příkazu **try-finally** , protože nedošlo k uvolnění zásobníku. Doporučujeme však použít klíčové slovo **__leave** , nikoli příkaz **goto** , protože v případě, že je chráněná část velká nebo složitá, je méně pravděpodobnější, že budou programové chyby.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Strukturované zpracování výjimek poskytuje dvě vnitřní funkce, které jsou k dispozici pro použití s příkazem **try-except** : `GetExceptionCode` a `GetExceptionInformation`.

`GetExceptionCode` vrátí kód (32 celé číslo) výjimky.

Vnitřní funkce `GetExceptionInformation` vrátí ukazatel na strukturu, která obsahuje další informace o výjimce. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následujícím způsobem:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy ukazatelů `PEXCEPTION_RECORD` a `PCONTEXT` jsou definovány v souboru include \<> Winnt. h a `_EXCEPTION_RECORD` a `_CONTEXT` jsou definovány v souboru include \<EXCPT. h >

Můžete použít `GetExceptionCode` v rámci obslužné rutiny výjimky. Můžete však použít `GetExceptionInformation` pouze v rámci výrazu filtru výjimky. Informace, na které ukazuje, jsou obecně umístěny do zásobníku a ve chvíli, kdy je řízení převedeno na obslužnou rutinu výjimky, jsou již nedostupné.

Vnitřní funkce `AbnormalTermination` je k dispozici v obslužné rutině ukončení. Vrátí 0, pokud tělo příkazu **try-finally** končí sekvenčně. Ve všech ostatních případech vrátí hodnotu 1.

EXCPT. h definuje některé alternativní názvy pro tyto vnitřní prvky:

`GetExceptionCode` je ekvivalentem `_exception_code`

`GetExceptionInformation` je ekvivalentem `_exception_info`

`AbnormalTermination` je ekvivalentem `_abnormal_termination`

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimky](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
