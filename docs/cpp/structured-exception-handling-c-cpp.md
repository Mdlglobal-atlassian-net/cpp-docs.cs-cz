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
ms.openlocfilehash: 942a7e48e4315454476bfe93c68169f461b006b2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245127"
---
# <a name="structured-exception-handling-cc"></a>Strukturované zpracování výjimek (C/C++)

Strukturované zpracování výjimek (SEH) je rozšíření společnosti Microsoft pro jazyk C, které zpracovává určité výjimečné situace v kódu, například hardwarové chyby, řádným způsobem. I když Windows a C++ Microsoft podporují SEH, doporučujeme, abyste používali zpracování výjimek C++ standardu ISO, protože díky tomu je váš kód lépe přenosný a flexibilní. Chcete-li však zachovat stávající kód nebo konkrétní druhy programů, bude pravděpodobně nutné použít SEH.

**Specifické pro společnost Microsoft:**

## <a name="grammar"></a>Gramatika

*try-except – příkaz* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *složený příkaz* **__except** **(** *výraz* **)**

*try-finally-příkaz* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *složený* příkaz **__finally** *složený* příkaz

## <a name="remarks"></a>Poznámky

Pomocí SEH můžete zajistit, aby prostředky, jako jsou paměťové bloky a soubory, byly vydány správně, pokud se provádění nečekaně ukončí. Můžete také zpracovat konkrétní problémy, například nedostatečné množství paměti – pomocí stručného strukturovaného kódu, který nespoléhá na příkazy **goto** nebo vést testování návratových kódů.

Příkazy try-except a try-finally uvedené v tomto článku jsou rozšířeními společnosti Microsoft pro jazyk C. Podporují SEH tím, že umožňují aplikacím převzít řízení programu po událostech, které by jinak ukončily provádění. I když SEH funguje C++ se zdrojovými soubory, není speciálně navržen pro C++. Použijete- C++ li SEH v programu, který kompilujete pomocí možnosti [/EHa nebo/EHsc](../build/reference/eh-exception-handling-model.md) , destruktory pro lokální objekty se nazývají, ale jiné chování při provádění nemusí být to, co očekáváte. Ilustraci najdete v příkladu dále v tomto článku. Ve většině případů místo SEH doporučujeme používat standardní [ C++ zpracování výjimek](../cpp/try-throw-and-catch-statements-cpp.md)standardu ISO, které kompilátor Microsoftu C++ podporuje i. Pomocí C++ zpracování výjimek můžete zajistit, aby byl kód lépe přenosný, a můžete zpracovat výjimky libovolného typu.

Pokud máte kód jazyka C, který používá SEH, můžete jej kombinovat s C++ kódem, který C++ používá zpracování výjimek. Informace naleznete v tématu [zpracování strukturovaných výjimek C++v ](../cpp/exception-handling-differences.md).

Existují dva mechanismy SEH:

- [Obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)nebo **__except** bloky, které mohou reagovat na nebo zrušit výjimku.

- [Obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)nebo **__finally** bloky, které jsou vždy volány, bez ohledu na to, zda výjimka způsobuje ukončení nebo ne.

Tyto dva druhy obslužných rutin jsou odlišné, ale úzce se vztahují k procesu, který se označuje jako "odvinutí zásobníku". Pokud dojde k strukturované výjimce, systém Windows vyhledá naposledy nainstalovanou obslužnou rutinu výjimky, která je aktuálně aktivní. Obslužná rutina může provést jednu ze tří věcí:

- Nepodařilo se rozpoznat výjimku a předat řízení jiným obslužným rutinám.

- Rozpoznat výjimku, ale zavřít ji.

- Rozpoznat výjimku a zpracovat ji.

Obslužná rutina výjimky, která rozpozná výjimku, nesmí být ve funkci, která byla spuštěna v okamžiku, kdy došlo k výjimce. V některých případech může být ve funkci mnohem vyšší v zásobníku. Aktuálně spuštěná funkce a všechny ostatní funkce v rámci rámce zásobníku jsou ukončeny. Během tohoto procesu je zásobník "Replaced;", což znamená, že místní nestatické proměnné ukončených funkcí jsou ze zásobníku vymazány.

Při uvolňování zásobníku volá operační systém jakékoli obslužné rutiny ukončení, které jste napsali pro jednotlivé funkce. Pomocí obslužné rutiny ukončení můžete vyčistit prostředky, které by jinak zůstaly otevřené z důvodu neobvyklého ukončení. Pokud jste zadali kritickou část, můžete ji ukončit v obslužné rutině ukončení. Pokud bude program vypnutý, můžete provádět další údržbu úlohy, jako je zavření a odebrání dočasných souborů.

## <a name="next-steps"></a>Další kroky

- [Zápis obslužné rutiny výjimky](../cpp/writing-an-exception-handler.md)

- [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)

- [Ošetření strukturovaných výjimek v C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Příklad

Jak bylo uvedeno dříve, destruktory pro lokální objekty jsou volány, pokud použijete C++ SEH v programu a zkompilujete pomocí možnosti **/EHa** nebo **/EHsc** . Chování při spuštění ale nemusí být očekávaným způsobem, pokud používáte i C++ výjimky. Tento příklad ukazuje tyto rozdíly v chování.

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

Použijete-li **/EHsc** pro zkompilování tohoto kódu, ale makro místního testovacího ovládacího prvku `CPPEX` není definováno, neexistuje žádné spuštění `TestClass` destruktoru a výstup vypadá takto:

```Output
Triggering SEH exception
Executing SEH __except block
```

Použijete-li **/EHsc** ke kompilaci kódu a `CPPEX` je definována pomocí `/DCPPEX` (takže je vyvolána C++ výjimka), spustí se destruktor `TestClass` a výstup vypadá takto:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Použijete-li **/EHa** ke kompilaci kódu, vykoná se `TestClass` destruktor bez ohledu na to, zda byla výjimka vyvolána pomocí `std::throw` nebo pomocí SEH k vyvolání výjimky, to znamená, zda `CPPEX` definována nebo nikoli. Výstup bude vypadat nějak takto:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Další informace naleznete v tématu [/EH (model zpracování výjimek)](../build/reference/eh-exception-handling-model.md).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[výjimka \<>](../standard-library/exception.md)<br/>
[Zpracování chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Strukturované zpracování výjimek (Windows)](/windows/win32/debug/structured-exception-handling)
