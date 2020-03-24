---
title: try, throw a catch – příkazy (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
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
ms.openlocfilehash: 03f7f6f5a1a2842ad7fb0ba2715fada130277e70
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187983"
---
# <a name="try-throw-and-catch-statements-c"></a>try, throw a catch – příkazy (C++)

Chcete-li implementovat zpracování C++výjimek v, použijte výrazy **Try**, **throw**a **catch** .

Nejprve použijte blok **Try** k uzavření jednoho nebo více příkazů, které mohou vyvolat výjimku.

Výraz **throw** signalizuje, že v bloku **Try** se vyskytla mimořádná podmínka – často chyba – došlo k chybě. Objekt libovolného typu můžete použít jako operand výrazu **throw** . Tento objekt je obvykle používán ke sdělování informací o dané chybě. Ve většině případů doporučujeme použít třídu [std:: Exception](../standard-library/exception-class.md) nebo jednu z odvozených tříd, které jsou definovány ve standardní knihovně. Pokud některý z těchto hodnot není vhodný, doporučujeme, abyste odvodili vlastní třídu výjimek z `std::exception`.

Chcete-li zpracovat výjimky, které mohou být vyvolány, implementujte jeden nebo více bloků **catch** ihned po bloku **Try** . Každý blok **catch** určuje typ výjimky, kterou může zpracovat.

Tento příklad ukazuje blok **Try** a jeho obslužné rutiny. Předpokládejme, že `GetNetworkResource()` získává data prostřednictvím síťového připojení a že jsou tyto dva typy výjimek uživatelsky definované třídy, které jsou odvozeny z `std::exception`. Všimněte si, že výjimky jsou zachyceny odkazem **const** v příkazu **catch** . Doporučujeme vyvolat výjimky podle hodnoty a zachytit jej podle odkazu const.

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

Kód za klauzulí **Try** je chráněný oddíl kódu. Výraz **throw** *vyvolá*– to znamená, že vyvolává výjimku. Blok kódu po klauzuli **catch** je obslužná rutina výjimky. Toto je obslužná rutina, která *zachycuje* výjimku, která je vyvolána, pokud jsou typy ve výrazech **throw** a **catch** kompatibilní. Seznam pravidel, která řídí porovnání typů v **catch** Blocks, najdete v tématu [jak jsou vyhodnocovány bloky catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Pokud příkaz **catch** určuje tři tečky (...) místo typu, blok **catch** zpracovává každý typ výjimky. Při kompilaci s možností [/EHa](../build/reference/eh-exception-handling-model.md) mohou zahrnovat strukturované výjimky jazyka C a systémem generované nebo generované asynchronní výjimky, jako je například ochrana paměti, dělení nulou a porušení plovoucí desetinné čárky. Vzhledem k tomu, že bloky **catch** jsou zpracovávány v pořadí programu za účelem nalezení odpovídajícího typu, musí být obslužná rutina tři tečky posledním popisovačem asociovaného bloku **Try** . Používejte `catch(...)` s opatrností; Nepovolit programu pokračovat, pokud blok catch neví, jak zpracovat konkrétní výjimku, která je zachycena. K protokolování chyb a provádění zvláštního vyčištění před zastavením spuštění programu se obvykle používá `catch(...)` blok.

Výraz **throw** , který nemá žádný operand znovu vyvolá výjimku, která je právě zpracovávána. Doporučujeme tento formulář při opětném vyvolávání výjimky, protože se tak zachovají informace o polymorfním typu původní výjimky. Takový výraz by měl být použit pouze v obslužné rutině **catch** nebo ve funkci, která je volána z obslužné rutiny **catch** . Objekt znovu vyvolané výjimky je původní objekt výjimky, ne kopie.

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

## <a name="see-also"></a>Viz také

[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Nezpracované výjimky jazyka C++](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
