---
title: Zkuste-except – příkaz | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af4d14eb3fad691a5ff10665a83879ae4319a3d9
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162032"
---
# <a name="try-except-statement"></a>try-except – příkaz

**Specifické pro Microsoft**

**Zkuste – s výjimkou** příkaz je rozšířením společnosti Microsoft pro C a C++ – jazyky, které podporuje strukturované zpracování výjimek.

## <a name="syntax"></a>Syntaxe

> **__try** <br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;strážené kódu<br/>
> }<br/>
> **__except** ( *výraz* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;Kód obslužné rutiny výjimek<br/>
> }<br/>

## <a name="remarks"></a>Poznámky

**Zkuste – s výjimkou** příkaz je rozšířením společnosti Microsoft pro C a C++ – jazyky, které umožňuje cílovým aplikacím získat řízení, pokud dojde k událostem, které za normálních okolností ukončí provádění programu. Tyto události jsou nazývány *výjimky*, a mechanismus, který se výjimkami zabývá, se nazývá *strukturované zpracování výjimek* (SEH).

Související informace naleznete v tématu [try-finally – příkaz](../cpp/try-finally-statement.md).

Výjimky mohou být hardwarové nebo softwarové. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro programy C++ je doporučeno použití mechanismu zpracování výjimek jazyka C++ ([try, catch a throw](../cpp/try-throw-and-catch-statements-cpp.md) příkazů).

Složený příkaz za **__try** klauzule je tělem nebo chráněnou částí. Složený příkaz za **__except** klauzule je obslužná rutina výjimky. Obslužná rutina udává sadu akcí provedených v případě, že během provádění těla chráněné části dojde k vyvolání výjimky. Spuštění probíhá následujícím způsobem:

1. Chráněná část je spuštěna.

1. Pokud při provádění chráněné části dojde k žádné výjimce, provádění pokračuje na příkazu následujícímu po **__except** klauzuli.

1. Pokud dojde k výjimce za běhu chráněné části nebo v jakékoli rutině chráněná část volá, **__except** *výraz* (volá se *filtr* výraz) je vyhodnocen a jeho hodnota určuje, jak je výjimka ošetřena. Existují tři možné hodnoty:

   - EXCEPTION_CONTINUE_EXECUTION (-1) výjimka je ignorována. Program bude pokračovat tam, kde k výjimce došlo.

   - EXCEPTION_CONTINUE_SEARCH (0) výjimka není rozpoznána. Pokračujte ve vyhledávání zásobníkem pro obslužnou rutinu, nejprve obsahující **zkuste – s výjimkou** příkazy, pak u obslužných rutin s druhou nejvyšší prioritou.

   - EXCEPTION_EXECUTE_HANDLER (1) výjimka je rozpoznána. Řízení je převedeno na obslužnou rutinu výjimek pomocí provádí **__except** složený příkaz a potom pokračovat v provádění po **__except** bloku.

Vzhledem k tomu, **__except** výraz je vyhodnocen jako výraz jazyka C, je omezený na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

Není povoleno přejít do **__try** příkaz však povoleno přejít mimo něj. Obslužná rutina výjimky není volána, pokud proces je ukončen v průběhu provádění příkazu **zkuste – s výjimkou** příkazu.

Z důvodu kompatibility s předchozími verzemi **_try**, **_except**, a **_leave** jsou synonyma pro **__try**, **__except** , a **__leave** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

### <a name="the-leave-keyword"></a>Klíčové slovo __leave

**__Leave** – klíčové slovo je platné pouze uvnitř chráněné části **zkuste – s výjimkou** příkazu a jeho účinkem je přechod na konec chráněné části. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

A **goto** příkaz lze také přejít mimo chráněnou část a nesnižuje výkon jako v **try-finally** příkaz protože odvíjení zásobníku nevyskytuje. Doporučujeme však, že používáte **__leave** – klíčové slovo spíše než **goto** příkaz vzhledem k tomu, že jste méně pravděpodobné, že aby programovací chyba, když chráněná část je velký nebo složitý.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Strukturované zpracování výjimek poskytuje dvě vnitřní funkce, které jsou k dispozici pro použití s **zkuste – s výjimkou** – příkaz: `GetExceptionCode` a `GetExceptionInformation`.

`GetExceptionCode` vrací kód výjimky (32bitové celé číslo).

Vnitřní funkce `GetExceptionInformation` vrací ukazatel na strukturu obsahující další informace o výjimce. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následující:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy ukazatelů `PEXCEPTION_RECORD` a `PCONTEXT` jsou definovány ve vloženém souboru \<souboru winnt.h >, a `_EXCEPTION_RECORD` a `_CONTEXT` jsou definovány ve vloženém souboru \<excpt.h >

Můžete použít `GetExceptionCode` uvnitř obslužné rutiny výjimky. Můžete však použít `GetExceptionInformation` pouze v rámci výrazu filtru výjimky. Informace, na které ukazuje, jsou obecně umístěny do zásobníku a ve chvíli, kdy je řízení převedeno na obslužnou rutinu výjimky, jsou již nedostupné.

Vnitřní funkce `AbnormalTermination` je k dispozici v rámci obslužné rutiny ukončení. Vrátí hodnotu 0, pokud text **try-finally** příkaz ukončeno sekvenčně. Ve všech ostatních případech vrátí hodnotu 1.

excpt.h definuje několik alternativních názvů pro tyto vnitřní objekty:

`GetExceptionCode` je ekvivalentní `_exception_code`

`GetExceptionInformation` je ekvivalentní `_exception_info`

`AbnormalTermination` je ekvivalentní `_abnormal_termination`

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
