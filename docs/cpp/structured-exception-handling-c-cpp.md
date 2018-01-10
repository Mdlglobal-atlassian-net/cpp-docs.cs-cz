---
title: "Strukturované zpracování výjimek (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 37d5a89ebf95d8852664dcd50e44e82009ebd95e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="structured-exception-handling-cc"></a>Strukturované zpracování výjimek (C/C++)
Přestože systém Windows a Visual C++ podporují strukturovaného zpracování (SEH) výjimek, doporučujeme použít zpracování výjimek C++ standardu ISO, protože umožňuje kód víc přenosného a flexibilní. Nicméně v existující kód nebo pro určité typy programů, můžete stále nejspíš muset použít SEH.  
  
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
## <a name="grammar"></a>Gramatika  
 *Zkuste s výjimkou příkaz* :  
  
 `__try`*složené – příkaz*  
  
 `__except`( `expression` ) *složené – příkaz*  
  
## <a name="remarks"></a>Poznámky  
 S SEH můžete zajistěte, aby byly prostředky třeba bloky paměti a soubory správně Pokud spouštění neočekávaně ukončena. Můžete také řešit konkrétní problémy – například nedostatek paměti – pomocí stručným strukturovaný kód, který není závislý na `goto` příkazy nebo vypracovala testování návratové kódy.  
  
 Try-except a try-finally – příkazy uvedené v tomto článku jsou rozšíření Microsoft pro jazyk C. Podporují SEH povolením aplikace převzít kontrolu nad program po události, které by jinak ukončení provádění. I když SEH funguje s C++ zdrojové soubory, je konkrétně není určená pro C++. Pokud použijete SEH zkompilujete pomocí programu C++ [/EH](../build/reference/eh-exception-handling-model.md) možnost – společně s určitým modifikátory – destruktory pro místní objekty se nazývají ale jiné chování při spuštění nemusí být očekávat. (Pro ilustraci, podívejte se na příklad později v tomto článku.) Ve většině případů místo SEH vám doporučujeme používat standardem ISO [zpracovávání výjimek v jazyce C++](../cpp/try-throw-and-catch-statements-cpp.md), který podporuje i Visual C++. Pomocí zpracovávání výjimek v jazyce C++, může zkontrolujte, zda váš kód je víc přenosného a můžete zpracování výjimek libovolného typu.  
  
 Pokud máte C moduly, které používají SEH, je možné kombinovat je s moduly C++ tohoto zpracování výjimek pomocí jazyka C++. Informace najdete v tématu [rozdíly ve zpracování výjimek](../cpp/exception-handling-differences.md).  
  
 Existují dvě SEH mechanismů:  
  
-   [Obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md), která reagovat na nebo zrušit výjimku.  
  
-   [Obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md), které jsou volány při výjimku způsobí ukončení v bloku kódu.  
  
 Tyto dva druhy obslužné rutiny jsou jedinečné, ale jsou úzce související prostřednictvím tento proces se označuje jako "unwinding zásobníku." Když dojde k výjimce, systém Windows hledá naposledy nainstalované obslužná rutina výjimky, který je aktuálně aktivní. Obslužná rutina provést jednu z následujících způsobů:  
  
-   Nepodařilo se rozpoznat výjimku a předá řízení ostatních obslužných rutin.  
  
-   Rozpoznat výjimku, ale zprávu zavřete.  
  
-   Rozpoznat výjimku a zpracovat je.  
  
 Obslužná rutina výjimky, který rozpoznává výjimka nemusí být ve funkci, která byla spuštěna, když se vyskytla výjimka. V některých případech může být ve funkci mnohem vyšší v zásobníku. Probíhající funkce a všechny funkce na rámec zásobníku budou ukončeny. Během tohoto procesu je zásobníku "oddělen"; to znamená, místní proměnné ukončenou funkcí – Pokud se nejedná o `static`– jsou vymazány ze zásobníku.  
  
 Jak ho unwinds zásobníku, operační systém volá všechny obslužné rutiny ukončení, které jste vytvořili pro každou funkci. Pomocí obslužné rutiny ukončení můžete vyčistit prostředky, které jinak by zůstala otevřít z důvodu abnormální ukončení. Pokud jste zadali kritická sekce, můžete ukončit v obslužné rutiny ukončení. Pokud budete programu vypnout, můžete provést další úlohy housekeeping například zavření a odebírání dočasných souborů.  
  
 Další informace naleznete v tématu:  
  
-   [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)  
  
-   [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)  
  
-   [Používání strukturovaného zpracování výjimek v jazyce C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>Příklad  
 Jak je uvedeno výše, destruktory pro místní objekty se volají, pokud používáte SEH v programu C++ a zkompilovat pomocí **/EH** možnost s určitým modifikátory – například **/EHsc** a   **/EHa**. Chování při spuštění však nemusí být toho, co očekáváte, pokud používáte také výjimky jazyka C++. Následující příklad ukazuje tyto chování rozdíly.  
  
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
  
 Pokud používáte **/EHsc** zkompilovat tento kód, ale ovládací prvek místního testovacího `CPPEX` je nedefinovaný, neexistuje žádný provádění `TestClass` destruktor a výstup vypadá jako tento:  
  
```Output  
Triggering SEH exception  
Executing SEH __except block  
```  
  
 Pokud používáte **/EHsc** zkompilovat kód a `CPPEX` se definuje pomocí `/DCPPEX` (tak, aby se výjimka C++), `TestClass` destruktor a výstup vypadá takto:  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Pokud používáte **/EHa** zkompilovat kód, `TestClass` destruktor bez ohledu na to, zda byla výjimka vydána pomocí `std::throw` nebo pomocí SEH k aktivaci výjimka (`CPPEX` definován nebo není). Výstup vypadá takto:  
  
```Output  
Throwing C++ exception  
Destroying TestClass!  
Executing SEH __except block  
```  
  
 Další informace najdete v tématu [/EH (Model zpracování výjimek)](../build/reference/eh-exception-handling-model.md).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [\<Výjimka >](../standard-library/exception.md)   
 [Ošetření chyb a výjimek](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Strukturované zpracování (Windows) výjimek](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)