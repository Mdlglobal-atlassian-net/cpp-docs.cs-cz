---
title: "Zkuste, throw a catch – příkazy (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
dev_langs:
- C++
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b100f1ee61b06639e75290fafd01dca6a10a820c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="try-throw-and-catch-statements-c"></a>try, throw a catch – příkazy (C++)
Chcete-li implementovat zpracování výjimek v C++, použijte `try`, `throw`, a `catch` výrazy.  
  
 Nejprve pomocí `try` blok k uzavřete jeden nebo více příkazů, které může vyvolat výjimku.  
  
 A `throw` signály výraz, který podmínku výjimečných – často chybu – došlo k chybě v `try` bloku. Objekt žádný typ, můžete použít jako operand `throw` výraz. Tento objekt je obvykle používán ke sdělování informací o dané chybě. Ve většině případů doporučujeme použít [std::exception](../standard-library/exception-class.md) třídy nebo některé z odvozené třídy, které jsou definovány ve standardní knihovně. Pokud jeden z nich není vhodná, doporučujeme odvozování vlastní třídy výjimek z `std::exception`.  
  
 Zpracování výjimek, které mohou být vyvolány, implementovat jednu nebo více `catch` bloky hned `try` bloku. Každý `catch` bloku Určuje typ výjimky může zpracovat.  
  
 Tento příklad ukazuje `try` bloku a jeho obslužné rutiny. Předpokládáme, že `GetNetworkResource()` získává data přes síťové připojení a že výjimky dva typy jsou uživatelem definované třídy, které jsou odvozeny od `std::exception`. Všimněte si, že výjimky jsou zachyceny pomocí `const` odkaz v `catch` příkaz. Doporučujeme vyvolat výjimky podle hodnoty a zachytit jej podle odkazu const.  
  
## <a name="example"></a>Příklad  
  
```  
  
MyData md;  
try {  
   // Code that could throw an exception  
   md = GetNetworkResource();  
}  
catch (const networkIOException& e) {  
   // Code that executes when an exception of type  
   // networkIOException is thrown in the try block  
   // ...  
   // Log error message in the exception object  
   cerr << e.what();  
}  
catch (const myDataFormatException& e) {  
   // Code that handles another exception type  
   // ...  
   cerr << e.what();  
}  
  
// The following syntax shows a throw expression  
MyData GetNetworkResource()  
{  
   // ...  
   if (IOSuccess == false)  
      throw networkIOException("Unable to connect");  
   // ...  
   if (readError)  
      throw myDataFormatException("Format error");   
   // ...  
}  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód po `try` chráněného oddíl kódu, je klauzule. `throw` Výraz *vyvolá*– to znamená, vyvolá – výjimku. Blok kódu po `catch` klauzule je obslužná rutina výjimky. Toto je obslužná rutina, *zachytí* výjimku, která je vyvolána, pokud typy v `throw` a `catch` výrazy jsou kompatibilní. Seznam pravidel, které řídí odpovídající v `catch` bloky, najdete v části [vyhodnocení jak bloků Catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Pokud `catch` příkaz určuje třemi tečkami (...) namísto typu, `catch` bloku zpracovává každý typ výjimky. Když kompilujete s [/EHa](../build/reference/eh-exception-handling-model.md) možnost, může jít o C strukturovaná a generována nebo generované aplikací asynchronní výjimek, jako je například paměť ochrany, dělení nulou a s plovoucí desetinnou čárkou porušení . Protože `catch` bloky se zpracovávají v pořadí program najít odpovídající typ, obslužné rutiny třemi tečkami musí být poslední obslužné rutiny pro přidruženého `try` bloku. Použití `catch(...)` opatrně; Nepovolit programu, chcete-li pokračovat, pokud blok catch umí zpracování konkrétní výjimku, která je zachycena. Obvykle `catch(...)` bloku se používá k protokolování chyb a provést čištění speciální před spuštění programu je zastavena.  
  
 A `throw` výraz, který nemá žádné operand znovu vyvolá výjimku aktuálně zpracovanou. Doporučujeme tento formulář při opětném vyvolávání výjimky, protože se tak zachovají informace o polymorfním typu původní výjimky. Takové výraz musí být použit pouze v `catch` obslužná rutina nebo ve funkci, která je volána z `catch` obslužné rutiny. Objekt znovu vyvolané výjimky je původní objekt výjimky, ne kopie.  
  
```  
try {  
   throw CSomeOtherException();  
}  
catch(...) {  
   // Catch all exceptions - dangerous!!!  
   // Respond (perhaps only partially) to the exception, then  
   // re-throw to pass the exception to some other handler  
   // ...  
   throw;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Nezpracované výjimky jazyka C++](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)