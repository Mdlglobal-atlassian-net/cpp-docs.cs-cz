---
title: příkaz try-except
description: Odkaz na příkazy zpracování __try a __except strukturované výjimky v jazyce Microsoft C++.
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
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366236"
---
# <a name="try-except-statement"></a>příkaz try-except

Příkaz **try-except** je rozšíření společnosti Microsoft, které podporuje strukturované zpracování výjimek v jazycích C a C++. Toto rozšíření je **specifické pro společnost Microsoft**.

## <a name="syntax"></a>Syntaxe

> **\_\_Zkuste**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;střežený kód<br/>
> }<br/>
> kromě ( *výraz* ) ** \_ \_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;kód obslužné rutiny výjimky<br/>
> }

## <a name="remarks"></a>Poznámky

Příkaz **try-except** je rozšíření microsoftu pro jazyky C a C++. Umožňuje cílovým aplikacím získat kontrolu, když dojde k událostem, které obvykle ukončí spuštění programu. Tyto události se nazývají *strukturované výjimky*nebo *výjimky* pro krátké. Mechanismus, který se zabývá těmito výjimkami se nazývá *strukturované zpracování výjimek* (SEH).

Související informace naleznete v [příkazu try-finally](../cpp/try-finally-statement.md).

Výjimky mohou být založené na hardwaru nebo softwaru. Strukturované zpracování výjimek je užitečné i v případě, že se aplikace nemohou zcela zotavit z výjimek hardwaru nebo softwaru. SEH umožňuje zobrazit informace o chybách a soutisk vnitřního stavu aplikace, které pomáhají diagnostikovat problém. To je užitečné zejména pro občasné problémy, které není snadné reprodukovat.

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Však není speciálně navržen pro C++. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro programy jazyka C++ doporučujeme použít nativní zpracování výjimek jazyka C++: [příkazy try, catch a throw.](../cpp/try-throw-and-catch-statements-cpp.md)

Složený příkaz po **klauzuli __try** je *tělo* nebo *chráněná* část. Výraz **__except** je také označován jako výraz *filtru.* Jeho hodnota určuje způsob zpracování výjimky. Složený příkaz po **klauzuli __except** je obslužná rutina výjimky. Obslužná rutina určuje akce, které mají být přijaty, pokud je během provádění části těla vyvolána výjimka. Exekuce probíhá takto:

1. Chráněná část je spuštěna.

1. Pokud dojde k žádné výjimce během provádění střežené části, provádění pokračuje na příkaz po **__except** klauzule.

1. Pokud dojde k výjimce během provádění hlídané části nebo v jakékoli rutině, kterou volá chráněná část, vyhodnotí **se __except** výraz. Existují tři možné hodnoty:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Výjimka je zamítnuta. Program bude pokračovat tam, kde k výjimce došlo.

   - `EXCEPTION_CONTINUE_SEARCH`(0) Výjimka není rozpoznána. Pokračujte v hledání do zásobníku pro obslužnou rutinu, nejprve pro obsahující **příkazy try-except,** pak pro obslužné rutiny s další nejvyšší prioritou.

   - `EXCEPTION_EXECUTE_HANDLER`(1) Výjimka je uznána. Přeneste řízení na obslužnou rutinu výjimky spuštěním **__except** složeného příkazu a pokračujte v provádění po **__except** bloku.

Výraz **__except** je vyhodnocen jako výraz Jazyka C. Je omezena na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

Každá aplikace může obsahovat svou vlastní obslužnou rutinu výjimky.

Není platné skočit do **__try** prohlášení, ale platí skočit z jednoho. Obslužná rutina výjimky není volána, pokud je proces ukončen uprostřed provádění příkazu **try-except.**

Pro kompatibilitu s předchozími verzemi jsou synonyma **_try pro** **__try** **_except**, **__except** **_leave** a **__leave,** pokud není zadána možnost kompilátoru [/Za \(zakázat jazykové rozšíření).](../build/reference/za-ze-disable-language-extensions.md)

### <a name="the-__leave-keyword"></a>Klíčové slovo __leave

Klíčové slovo **__leave** je platné pouze v rámci střežené části příkazu **try-except** a jeho účinkem je přechod na konec střežené části. Běh programu pokračuje prvním příkazem za obslužnou rutinou výjimky.

Příkaz **goto** může také vyskočit z hlídané části a nesnižuje výkon stejně jako v příkazu **try-finally.** To proto, že zásobník odvíjení nedochází. Doporučujeme však použít **klíčové** slovo __leave spíše než příkaz **goto.** Důvodem je, že je méně pravděpodobné, že uděláte programovou chybu, pokud je chráněná část velká nebo složitá.

### <a name="structured-exception-handling-intrinsic-functions"></a>Vnitřní funkce strukturovaného zpracování výjimek

Strukturované zpracování výjimek poskytuje dvě vnitřní funkce, které jsou k dispozici pro použití s **příkazem try-except:** [GetExceptionCode](/windows/win32/Debug/getexceptioncode) a [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`vrátí kód (32bitové celé číslo) výjimky.

Vnitřní funkce `GetExceptionInformation` vrátí ukazatel na [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) strukturu obsahující další informace o výjimce. Pomocí tohoto ukazatele lze přistoupit ke stavu počítače, v jakém byl v době výskytu hardwarové výjimky. Struktura je následující:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Body ukazatele `PEXCEPTION_RECORD` `PCONTEXT` a jsou definovány \<v souboru include `_EXCEPTION_RECORD` `_CONTEXT` winnt.h> \<a jsou definovány v souboru zahrnutí excpt.h>

Můžete použít `GetExceptionCode` v rámci obslužné rutiny výjimky. Můžete však `GetExceptionInformation` použít pouze v rámci výrazu filtru výjimky. Informace, na které odkazuje, jsou obecně v zásobníku a již nejsou k dispozici, když se ovládací prvek přenese na obslužnou rutinu výjimky.

Vnitřní funkce [AbnormalTermination](/windows/win32/Debug/abnormaltermination) je k dispozici v rámci obslužné rutiny ukončení. Vrátí hodnotu 0, pokud tělo příkazu **try-finally** postupně ukončí. Ve všech ostatních případech vrátí hodnotu 1.

\<excpt.h> definuje některé alternativní názvy pro tyto vnitřní objekty:

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
