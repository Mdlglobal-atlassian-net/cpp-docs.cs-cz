---
title: "try-finally – příkaz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs: C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c57676cace8451de266d30d4c146e3ae0c3cb1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="try-finally-statement"></a>try-finally – příkaz
**Konkrétní Microsoft**  
  
 Popisuje syntaxi `try-finally` příkaz:  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>Gramatika  
 *try-finally – příkaz*:  
 `__try`*složené – příkaz*  
  
 `__finally`*složené – příkaz*  
  
 `try-finally` Příkaz je rozšíření Microsoft pro jazyky C a C++, která umožňuje aplikacím cíl zaručit spuštění kódu čištění, když dojde k přerušení spuštění bloku kódu. Čištění se skládá z úlohy, jako jsou rušení přidělení paměti, zavírání souborů a uvolněním popisovače souborů. `try-finally` Příkaz je zvláště užitečná pro rutiny, které mají několika místech, kde je provedena kontrola pro chybu, která by mohla způsobovat předčasné vrátit z rutiny.  
  
 Ukázka kódu a související informace najdete v tématu [zkuste-except – příkaz](../cpp/try-except-statement.md). Další informace o strukturovaného zpracování obecně výjimek najdete v tématu [strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Další informace o zpracování výjimek ve spravovaných aplikacích najdete v tématu [zpracování výjimek v/CLR](../windows/exception-handling-cpp-component-extensions.md).  
  
> [!NOTE]
>  Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. C++ – programy, se doporučuje použít mechanismus zpracování výjimek C++ ([akci, zachytit a vyvolat](../cpp/try-throw-and-catch-statements-cpp.md) příkazy).  
  
 Složený příkaz po `__try` části chráněného je klauzule. Složený příkaz po `__finally` je klauzule obslužné rutiny ukončení. Obslužná rutina určuje sadu akcí, které spustit, když byl ukončen části chráněného, bez ohledu na to, jestli je k výjimce (abnormální ukončení), nebo standardní patří prostřednictvím (normální ukončení) byl ukončen chráněného oddílu.  
  
 Řízení dosáhnou `__try` příkaz podle jednoduchý sekvenční provádění (patří prostřednictvím). Pokud vstoupí do ovládacího prvku `__try`, jeho přidruženou obslužnou rutinu stane aktivní. Pokud toku řízení dosáhne konce bloku try, provádění pokračuje následujícím způsobem:  
  
1.  Obslužné rutiny ukončení je volána.  
  
2.  Po dokončení obslužné rutiny ukončení pokračuje po spuštění `__finally` příkaz. Bez ohledu na to, jak budou dát části končí (například prostřednictvím `goto` z chráněného obsahu nebo `return` příkaz), je proveden obslužné rutiny ukončení `before` toku řízení přesune mimo části chráněného.  
  
     A **__finally** příkaz neblokuje vyhledávání pro obslužnou rutinu příslušné výjimky.  
  
 Pokud dojde k výjimce v `__try` bloku, operační systém musí najít obslužnou rutinu výjimky nebo program se nezdaří. Pokud obslužná rutina najde, veškeré `__finally` provedení bloky a provádění pokračuje v obslužné rutině.  
  
 Předpokládejme například, řadu volání funkce odkazy funkce A funkci D, jak je znázorněno na následujícím obrázku. Jednotlivé funkce má jeden obslužné rutiny ukončení. Pokud místo vyvolání funkce D a zpracovány ve A výjimka obslužné rutiny ukončení se říká v tomto pořadí systému unwinds zásobníku: D, C, B.  
  
 ![Pořadí ukončení & č. 45; obslužná rutina provádění](../cpp/media/vc38cx1.gif "vc38CX1")  
Pořadí provádění obslužné rutiny ukončení  
  
> [!NOTE]
>  Chování try-finally – se liší od jiných jazycích, které podporují použití **nakonec**, například C#.  Jediný `__try` může mít buď, ale ne obojí z `__finally` a `__except`.  Pokud jsou obě použít společně, vnější zkuste – s výjimkou příkaz musí uzavřete vnitřní try-finally – příkaz.  Pravidla určující, když každý blok provede se také liší.  
  
## <a name="the-leave-keyword"></a>Klíčové slovo __leave  
 Klíčové slovo `__leave` je platné pouze uvnitř chráněné části příkazu `try-finally` a jeho účinkem je přechod na konec chráněné části. Provádění pokračuje na prvním příkazem v obslužné rutiny ukončení.  
  
 A `goto` příkaz můžete také přejít z části chráněného, ale snižuje výkon, protože vyvolá uvolnění zásobníku. `__leave` Příkaz je efektivnější, protože nezpůsobí uvolnění zásobníku.  
  
## <a name="abnormal-termination"></a>Abnormální ukončení  
 Ukončení `try-finally` příkaz pomocí [longjmp](../c-runtime-library/reference/longjmp.md) běhové funkce považuje za abnormální ukončení. Není povolen přejít do `__try` prohlášení, ale právní přejít od jednoho. Všechny `__finally` příkazy, které jsou aktivní mezi bodem odeslání (normální ukončení `__try` blok) a cíl ( `__except` blok, který zpracovává výjimku) musí být spuštěn. Tomu se říká místní unwind.  
  
 Pokud **zkuste** bloku je předčasně ukončen z jakéhokoli důvodu, včetně přechod z bloku, systém provede přidruženého **nakonec** blok jako součást procesu unwinding zásobníku. V takových případech [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265) funkce vrátí hodnotu TRUE, pokud je volána v rámci **nakonec** blokovat; jinak vrátí hodnotu FALSE.  
  
 Obslužné rutiny ukončení není volána, pokud je tento proces se ukončil uprostřed provádění `try-finally` příkaz.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Syntaxe obslužné rutiny ukončení](http://msdn.microsoft.com/library/windows/desktop/ms681393)