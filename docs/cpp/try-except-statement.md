---
title: příkaz try-except
description: Odkaz Microsoft C++ na __try a __except příkazy pro zpracování strukturovaných výjimek.
ms.date: 04/03/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
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
ms.openlocfilehash: d0471bbd50e07fccbf160e9e866de4c545cdeb7e
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825767"
---
# <a name="try-except-statement"></a>příkaz try-except

Příkaz **try-except** je rozšířením společnosti Microsoft, které podporuje zpracování strukturované výjimky v jazycích C a C++. Toto rozšíření je **specifické pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

> **\_\_Zkuste**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;chráněný kód \
> }\
> výjimkou ( *výraz* ) \ ** \_ \_**
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;kód obslužné rutiny výjimky \
> }

## <a name="remarks"></a>Poznámky

Příkaz **try-except** je rozšířením společnosti Microsoft pro jazyky C a C++. Umožňuje cílovým aplikacím získat kontrolu nad tím, kdy dojde k událostem, které obvykle ukončí provádění programu. Tyto události se nazývají *strukturované výjimky*nebo *výjimky* pro krátké. Mechanismus, který se zabývá těmito výjimkami, se nazývá *zpracování strukturované výjimky* (SEH).

Související informace naleznete v [příkazu try-finally](../cpp/try-finally-statement.md).

Výjimky mohou být založené na hardwaru nebo softwaru. Strukturované zpracování výjimek je užitečné i v případě, že se aplikace nemůžou úplně zotavit z hardwarových nebo softwarových výjimek. SEH umožňuje zobrazit informace o chybě a zachytit vnitřní stav aplikace, aby bylo možné problém diagnostikovat. To je zvlášť užitečné pro přerušované problémy, které není snadné reprodukování.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Není však navržena konkrétně pro jazyk C++. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro programy C++ doporučujeme použít nativní zpracování výjimek v jazyce C++: příkazy [Try, Catch a throw](../cpp/try-throw-and-catch-statements-cpp.md) .

Složený příkaz za klauzulí **__try** je *tělo* nebo *chráněný* oddíl. Výraz **__except** se také označuje jako výraz *filtru* . Jeho hodnota určuje, jak je výjimka zpracována. Složený příkaz za klauzulí **__except** je obslužná rutina výjimky. Obslužná rutina určuje akce, které se mají provést, pokud se při provádění oddílu tělo vyvolá výjimka. Provádění pokračuje následujícím způsobem:

1. Chráněná část je spuštěna.

1. Pokud během provádění chráněné části nedojde k žádné výjimce, vykonání pokračuje v příkazu za klauzulí **__except** .

1. Pokud dojde k výjimce během provádění chráněné části nebo v jakékoli rutině chráněného oddílu, je vyhodnocen výraz **__except** . Existují tři možné hodnoty:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Výjimka byla zrušena. Program bude pokračovat tam, kde k výjimce došlo.

   - `EXCEPTION_CONTINUE_SEARCH`(0) výjimka nebyla rozpoznána. Pokračujte v hledání zásobníku pro obslužnou rutinu, nejprve pro příkazy **try-except** a potom pro obslužné rutiny s další nejvyšší prioritou.

   - `EXCEPTION_EXECUTE_HANDLER`(1) výjimka je rozpoznána. Převeďte řízení na obslužnou rutinu výjimky spuštěním složeného příkazu **__except** a potom pokračujte v provádění po bloku **__except** .

Výraz **__except** je vyhodnocen jako výraz jazyka C. Je omezen na jedinou hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

Skok na příkaz **__try** není platný, ale je platný pro skok mimo jeden. Obslužná rutina výjimky není volána, pokud je proces ukončen uprostřed provádění příkazu **try-except** .

Z důvodu kompatibility s předchozími verzemi jsou **_try**, **_except**a **_leave** synonyma pro **__try**, **__except**a **__leave** , pokud je zadána možnost kompilátoru [ \(/za Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

### <a name="the-__leave-keyword"></a>Klíčové slovo __leave

Klíčové slovo **__leave** je platné pouze v rámci chráněné části příkazu **try-except** a jeho efekt je přejít na konec chráněné části. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

Příkaz **goto** může také přejít mimo chráněný oddíl a nesnižuje výkon, protože v příkazu **try-finally** . Důvodem je to, že k uvolnění zásobníku nedochází. Doporučujeme však použít klíčové slovo **__leave** , nikoli příkaz **goto** . Důvodem je, že v případě, že je chráněná část velká nebo složitá, je méně pravděpodobnější, že dojde k programové chybě.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Strukturované zpracování výjimek poskytuje dvě vnitřní funkce, které jsou k dispozici pro použití s příkazem **try-except** : [GetExceptionCode](/windows/win32/Debug/getexceptioncode) a [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`Vrátí kód (32 celé číslo) výjimky.

Vnitřní funkce `GetExceptionInformation` vrací ukazatel na [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) strukturu obsahující další informace o výjimce. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následující:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Typy `PEXCEPTION_RECORD` ukazatelů a `PCONTEXT` jsou definovány v souboru \<include Winnt. h> a `_EXCEPTION_RECORD` a `_CONTEXT` jsou definovány v souboru \<include EXCPT. h>

Můžete použít `GetExceptionCode` v rámci obslužné rutiny výjimky. Můžete však použít `GetExceptionInformation` pouze v rámci výrazu filtru výjimky. Informace, na které odkazuje, jsou obecně v zásobníku a již nejsou k dispozici, pokud je ovládací prvek převeden do obslužné rutiny výjimky.

Vnitřní funkce [AbnormalTermination](/windows/win32/Debug/abnormaltermination) je k dispozici v obslužné rutině ukončení. Vrátí 0, pokud tělo příkazu **try-finally** končí sekvenčně. Ve všech ostatních případech vrátí hodnotu 1.

\<EXCPT. h> definuje některé alternativní názvy pro tyto vnitřní prvky:

`GetExceptionCode`je ekvivalentem`_exception_code`

`GetExceptionInformation`je ekvivalentem`_exception_info`

`AbnormalTermination`je ekvivalentem`_abnormal_termination`

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

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny výjimky](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
