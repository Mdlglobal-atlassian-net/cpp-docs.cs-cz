---
title: "Zkuste-except – příkaz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24be4e7fd6b4dc95d9964e69943a94ecad947a47
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="try-except-statement"></a>try-except – příkaz

**Microsoft Specific**  
**Zkuste – s výjimkou** příkaz je rozšíření Microsoft pro C a C++ jazyky, které podporuje strukturované zpracování výjimek.  

## <a name="syntax"></a>Syntaxe  
  
> **__try**   
> {  
>    chráněného kódu  
> }  
> **__except** ( *výraz* )  
> {  
>    Kód obslužné rutiny výjimek  
> }  

## <a name="remarks"></a>Poznámky

**Zkuste – s výjimkou** příkaz je rozšíření Microsoft pro C a C++ jazyky, které umožňuje aplikacím cíl k získání řízení, pokud dojde k události, které obvykle ukončit spuštění programu. Tyto události se nazývají *výjimky*, a tento mechanismus, který se zabývá výjimky se nazývá *strukturovanému zpracování výjimek* (SEH).

Související informace najdete v tématu [try-finally – příkaz](../cpp/try-finally-statement.md).

Výjimky mohou být hardwarové nebo softwarové. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. C++ – programy, se doporučuje použít mechanismus zpracování výjimek C++ ([akci, zachytit a vyvolat](../cpp/try-throw-and-catch-statements-cpp.md) příkazy).

Složený příkaz za klauzulí `__try` je tělem nebo chráněnou částí. Složený příkaz po klauzuli `__except` je obslužnou rutinou výjimky. Obslužná rutina udává sadu akcí provedených v případě, že během provádění těla chráněné části dojde k vyvolání výjimky. Provádění pokračuje následujícím způsobem:

1. Chráněná část je spuštěna.

2. Nedojde-li za běhu chráněné části k žádné výjimce, pokračuje běh programu příkazem za klauzulí `__except`.  

3. Pokud dojde k výjimce během zpracování oddílu chráněného nebo v jakékoli rutině části chráněného volá, `__except` *výraz* (volat *filtru* výrazu) je vyhodnocena a hodnotu Určuje, jak je výjimka ošetřena. Existují tři hodnoty:

   **Exception_continue_execution – (-1)** výjimka se zavře. Program bude pokračovat tam, kde k výjimce došlo.

   **Exception_continue_search – (0)** výjimky nebyl rozpoznán. Pokračovat ve vyhledávání nahoru v zásobníku pro obslužnou rutinu, nejdřív pro obsahující **zkuste – s výjimkou** příkazy, pak pro obslužné rutiny s další nejvyšší prioritou.

   **Exception_execute_handler – (1)** se rozpozná výjimka. Řízení je převedeno na obslužnou rutinu událostí spuštěním složeného příkazu `__except`, poté běh programu pokračuje příkazy za blokem `__except`.

Protože `__except` výraz vyhodnocen jako výraz C, je omezený na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárka. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

Není povoleno přejít do příkazu `__try`, je však povoleno přejít mimo něj. Obslužná rutina výjimky není volána, pokud proces, je ukončen uprostřed provádění **zkuste – s výjimkou** příkaz.  
  
Další informace naleznete v článku Q315937 znalostní báze: POSTUP: Zachycení přetečení zásobníku v aplikaci Visual C++.  
  
## <a name="the-leave-keyword"></a>Klíčové slovo __leave

`__leave` – Klíčové slovo je platná pouze v rámci části chráněného **zkuste – s výjimkou** prohlášení a jeho dopad je chcete přejít na konci chráněného části. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

A `goto` příkaz můžete také přejít z části chráněného a nesnižuje výkon, jako je tomu v **try-finally –** příkaz protože uvolnění zásobníku nedojde. Je však doporučeno používat spíše klíčové slovo `__leave` namísto příkazu `goto`, protože tím lze snížit riziko programové chyby, je-li chráněný oddíl velký nebo složitý.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Strukturované zpracování výjimek poskytuje dva vnitřní funkce, které jsou k dispozici pro použití s **zkuste – s výjimkou** příkaz: `GetExceptionCode` a `GetExceptionInformation`.

`GetExceptionCode`vrátí kód (32bitové celé číslo) výjimky.

Vnitřní funkce `GetExceptionInformation` vrací ukazatel na strukturu obsahující další informace o výjimce. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následující:

```cpp  
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS; 
```  

Typy ukazatelů `PEXCEPTION_RECORD` a `PCONTEXT` jsou definovány v souboru zahrnout \<souboru winnt.h >, a `_EXCEPTION_RECORD` a `_CONTEXT` jsou definovány v souboru zahrnout \<excpt.h >

Můžete použít `GetExceptionCode` v rámci obslužná rutina výjimky. Můžete však použít `GetExceptionInformation` pouze v rámci výrazu filtru výjimek. Informace, na které ukazuje, jsou obecně umístěny do zásobníku a ve chvíli, kdy je řízení převedeno na obslužnou rutinu výjimky, jsou již nedostupné.

Vnitřní funkce `AbnormalTermination` je k dispozici v rámci obslužné rutiny ukončení. Pokud vrátí hodnotu 0 text **try-finally –** příkaz ukončí postupně. Ve všech ostatních případech vrátí hodnotu 1.

excpt.h definuje některé alternativní názvy pro vnitřní tyto funkce:

`GetExceptionCode`je ekvivalentní`_exception_code`

 `GetExceptionInformation`je ekvivalentní`_exception_info`

 `AbnormalTermination`je ekvivalentní`_abnormal_termination`
  
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
  
## <a name="output"></a>Výstup  
  
```  
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

**Konkrétní Microsoft END**  

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
[Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)   
[Klíčová slova](../cpp/keywords-cpp.md)
