---
title: Strukturované zpracování výjimek (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: b77a218340399578e3c9428100476787e2e60b25
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330567"
---
# <a name="structured-exception-handling-cc"></a>Strukturované zpracování výjimek (C/C++)

Strukturované zpracování výjimek (SEH) je rozšířením společnosti Microsoft pro C elegantně zpracovat určité situace výjimečných kódu, například hardwarových chyb. I když Windows a Visual C++ podporují SEH, doporučujeme použít zpracování výjimek jazyka C++ podle standardu ISO, protože je váš kód větší přenositelnosti a flexibility. Nicméně chcete-li zachovat stávající kód nebo v určitých typech programů, stále může být nutné použít SEH.

**Specifické pro Microsoft:**

## <a name="grammar"></a>Gramatika

*s výjimkou příkazu Try* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__except** **(** *výraz* **)** *compound-statement*

*try-finally-statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__finally** *compound-statement*

## <a name="remarks"></a>Poznámky

Spolu se SEH můžete zajistit, že prostředky, jako jsou bloky paměti a soubory jsou správně uvolněny, pokud neočekávaně ukončí provádění. Můžete také zpracovávat specifické problémy – třeba nedostatek paměti – s použitím stručné strukturovaný kód, který nevyžaduje **goto** příkazy nebo propracované testování návratové kódy.

Try-except a try-finally příkazy uvedené v tomto článku jsou rozšíření Microsoft pro jazyk C. Tím, že umožňuje aplikacím získat kontrolu nad programu po události, které by jinak ukončí provádění podporují SEH. Přestože SEH funguje s zdrojových souborů C++, není výslovně navrženo pro jazyk C++. Pokud používáte SEH v programu C++ pro kompilaci pomocí [/EHa nebo/EHsc](../build/reference/eh-exception-handling-model.md) možnost, destruktory pro místní objekty jsou volány, ale nemusí být jiné chování při spuštění, co očekáváte. Pro ilustraci podívejte se na příklad dále v tomto článku. Ve většině případů místo SEH vám doporučujeme použít standardu ISO [zpracování výjimek jazyka C++](../cpp/try-throw-and-catch-statements-cpp.md), které Visual C++ podporuje také. S použitím zpracování výjimek jazyka C++, můžete zajistit, že váš kód je větší přenositelnost a dokáže zpracovat výjimky libovolného typu.

Pokud máte kód jazyka C, který používá SEH, je možné ji kombinovat s kódem jazyka C++, který používá zpracování výjimek jazyka C++. Informace najdete v tématu [zpracování strukturovaných výjimek v jazyce C++](../cpp/exception-handling-differences.md).

Existují dva mechanismy SEH:

- [Obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md), nebo **__except** bloků, které může reagovat na nebo zrušit výjimku.

- [Obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md), nebo **__finally** bloků, které jsou vždy volány, zda výjimku způsobí ukončení, nebo ne.

Tyto dva typy obslužných rutin se liší, ale jsou úzce související s procesem, který se označuje jako "odvíjení zásobníku." Pokud se strukturovaná výjimka objeví, hledá Windows nedávno nainstalované obslužná rutina výjimky, která je aktuálně aktivní. Obslužná rutina můžete provést jednu z tři věci:

- Nepovedlo se rozpoznat výjimku a předá řízení jiné obslužné rutině.

- Rozpoznat výjimku, ale zavřít.

- Rozpoznat výjimku a zpracoval ji.

Obslužná rutina výjimky, která rozpozná výjimku nemusí být ve funkci, která byla spuštěna, kde došlo k výjimce. V některých případech může být ve funkci v zásobníku mnohem vyšší. Aktuálně spuštěné funkce a všechny funkce v zásobníku, budou ukončeny. Během tohoto procesu je zásobník "odvinut"; to znamená, místní proměnné nestatické ukončené funkce jsou vymazány ze zásobníku.

Jak ji unwinds zásobníku, operační systém zavolá libovolné obslužné rutiny ukončení, které jste zadali pro každou funkci. Když použijete obslužné rutiny ukončení, můžete vyčistit prostředky, které jinak by zůstaly otevřené z důvodu abnormální ukončení. Pokud jste zadali kritický oddíl, můžete ho ukončit v obslužné rutiny ukončení. Pokud chcete vypnout program, můžete provádět další úlohy údržby pořádku jako je například zavření a odebírání dočasných souborů.

## <a name="next-steps"></a>Další kroky

- [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)

- [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)

- [Ošetření strukturovaných výjimek v C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Příklad

Jak je uvedeno výše, destruktory pro místní objekty se volají, pokud SEH lze použít v programu v jazyce C++ a jeho kompilace pomocí **/EHa** nebo **/EHsc** možnost. Chování za běhu však nemusí být co očekáváte, že pokud také používáte výjimky jazyka C++. Tento příklad znázorňuje tyto behaviorální rozdíly.

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

Pokud používáte **/EHsc** ke kompilaci tohoto kódu, ale ovládací prvek makro místního testovacího `CPPEX` je nedefinovaný, neexistuje žádný provádění `TestClass` destruktor a výstup vypadá takto:

```Output
Triggering SEH exception
Executing SEH __except block
```

Pokud používáte **/EHsc** pro kompilaci kódu a `CPPEX` se definuje pomocí `/DCPPEX` (tak, že je vyvolána výjimka jazyka C++), `TestClass` destruktor a výstup vypadá takto:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Pokud používáte **/EHa** ke kompilaci kódu, `TestClass` bez ohledu na to, zda byla výjimka vydána pomocí provádí – destruktor `std::throw` nebo s použitím SEH aktivuje výjimku, to znamená, zda `CPPEX` definované nebo není. Výstup vypadá takto:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Další informace najdete v tématu [/EH (Model zpracování výjimek)](../build/reference/eh-exception-handling-model.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[(Windows) pro zpracování strukturovaných výjimek](https://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)
