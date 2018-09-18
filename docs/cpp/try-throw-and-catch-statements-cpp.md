---
title: Try, throw a catch – příkazy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8454df8f8f66264e1e877a1e1504f4266944fa7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118892"
---
# <a name="try-throw-and-catch-statements-c"></a>try, throw a catch – příkazy (C++)

K implementaci zpracování výjimek v C++, můžete použít **zkuste**, **throw**, a **catch** výrazy.

Nejprve **zkuste** bloku uzavřete jeden nebo více příkazů, které mohou vyvolat výjimku.

A **throw** výraz signalizuje, že výjimečné podmínce – často chybě – došlo k chybě v **zkuste** bloku. Objekt jakéhokoli typu můžete použít jako operand **throw** výrazu. Tento objekt je obvykle používán ke sdělování informací o dané chybě. Ve většině případů doporučujeme použít [std::exception](../standard-library/exception-class.md) třídy nebo některé z odvozených tříd, které jsou definovány ve standardní knihovně. Pokud jeden z nich není vhodná, doporučujeme odvodit vlastní třídu výjimek z `std::exception`.

Zpracování výjimek, které mohou být vyvolány, implementujte jeden nebo více **catch** bloky hned za **zkuste** bloku. Každý **catch** bloku Určuje typ výjimky, které dokáže zpracovat.

Tento příklad ukazuje **zkuste** bloku a jeho obslužné rutiny. Předpokládejme, že `GetNetworkResource()` získává data přes síťové připojení a že tyto dva typy výjimek jsou třídy definované uživatelem, které jsou odvozeny z `std::exception`. Všimněte si, že tyto výjimky jsou zachyceny pomocí **const** odkazovat **catch** příkazu. Doporučujeme vyvolat výjimky podle hodnoty a zachytit jej podle odkazu const.

## <a name="example"></a>Příklad

```cpp
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

Kód za **zkuste** klauzule je chráněná část kódu. **Throw** výraz *vyvolá*– to znamená, vyvolá – výjimku. Blok kódu po **catch** klauzule je obslužná rutina výjimky. To je obslužná rutina, která *zachytí* výjimku, která je vyvolána, pokud typy ve **throw** a **catch** výrazy jsou kompatibilní. Seznam pravidel, která určují typ shody v **catch** bloky, naleznete v tématu [How Catch Blocks vyhodnocují](../cpp/how-catch-blocks-are-evaluated-cpp.md). Pokud **catch** příkaz určuje tři tečky (...) místo typu, **catch** bloku zpracovává každý typ výjimky. Pokud kompilujete s [/EHa](../build/reference/eh-exception-handling-model.md) možnost, může jít o strukturované výjimky jazyka C a systémem či aplikacemi generované asynchronní výjimky, jako je paměť ochrany, dělení nulou a s plovoucí desetinnou čárkou porušení . Protože **catch** bloky se zpracovávají v pořadí programu se najít odpovídající typ, obslužná rutina tří teček musí být poslední obslužnou rutinou pro přidružený **zkuste** bloku. Použití `catch(...)` používejte opatrně neumožňují programu pokračovat, dokud blok catch ví, jak zpracovat určitou výjimku, která je zachycena. Obvykle `catch(...)` blokování se používá k protokolování chyb a provádění zvláštního vyčištění před zastavením spuštění programu.

A **throw** výraz, který nemá žádné operandy, znovu vyvolá aktuálně zpracovávanou výjimku. Doporučujeme tento formulář při opětném vyvolávání výjimky, protože se tak zachovají informace o polymorfním typu původní výjimky. Takový výraz byste měli použít pouze ve **catch** obslužné rutiny nebo ve funkci, která je volána z **catch** obslužné rutiny. Objekt znovu vyvolané výjimky je původní objekt výjimky, ne kopie.

```cpp
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

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Nezpracované výjimky jazyka C++](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)