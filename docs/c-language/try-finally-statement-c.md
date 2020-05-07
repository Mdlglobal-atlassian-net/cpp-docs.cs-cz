---
title: try-finally – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 61a6a9edd9faaf8afb06bb7bfdc619cddde3e6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349603"
---
# <a name="try-finally-statement-c"></a>try-finally – příkaz (C)

**Specifické pro Microsoft**

`try-finally` Příkaz je rozšířením společnosti Microsoft pro jazyk C, které umožňuje aplikacím zaručit spuštění kódu pro vyčištění v případě přerušení běhu bloku kódu. Vyčištění se skládá z těchto úloh jako rušení přidělení paměti, zavírání souborů a uvolňování obslužných rutin souborů. `try-finally` Příkaz je zvláště užitečný pro rutiny, které mají několik míst, kde je provedena kontrola chyby, která by mohla způsobit předčasné vrácení z rutiny.

*try-finally-příkaz*: **__try***složený* příkaz  

**__finally***složený* příkaz  

Složený příkaz za `__try` klauzulí je chráněný oddíl. Složený příkaz za `__finally` klauzulí je obslužná rutina ukončení. Obslužná rutina určuje sadu akcí, které se spustí při ukončení chráněného oddílu, bez ohledu na to, jestli je chráněný oddíl ukončený výjimkou (abnormální ukončení) nebo podle standardu (normální ukončení).

Ovládací prvek dosáhne `__try` příkazu jednoduchým sekvenčním spouštěním (Přejít do). Když ovládací prvek vstoupí `__try` do příkazu, jeho přidružená obslužná rutina se stane aktivní. Provádění pokračuje následujícím způsobem:

1. Chráněná část je spuštěna.

1. Je vyvolána obslužná rutina ukončení.

1. Po dokončení obslužné rutiny ukončení pokračuje provádění i po `__finally` příkazu. Bez ohledu na to, jak chráněná část končí (například prostřednictvím `goto` příkazu z chráněného těla nebo prostřednictvím `return` příkazu), je obslužná rutina ukončení provedena před tím, než se tok řízení přesune mimo chráněný oddíl.

`__leave` Klíčové slovo je platné v rámci `try-finally` bloku příkazu. Efekt `__leave` je přejít na konec `try-finally` bloku. Obslužná rutina ukončení se okamžitě spustí. Přestože lze `goto` použít příkaz k dosažení stejného výsledku, `goto` příkaz způsobí unwind zásobníku. `__leave` Příkaz je efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení `try-finally` příkazu pomocí `return` příkazu nebo funkce za `longjmp` běhu se považuje za abnormální ukončení. Je neplatné přeskočit do `__try` příkazu, ale právním přechodem na jeden z nich. Všechny `__finally` příkazy, které jsou aktivní mezi bodem odeslání a cílovým umístěním, musí být spuštěny. Toto se nazývá "místní unwind".

Obslužná rutina ukončení není volána, pokud je proces ukončen při spuštění `try-finally` příkazu.

> [!NOTE]
> Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Mechanismus zpracování výjimek jazyka C++ je také mnohem flexibilní, v tom případě může zpracovávat výjimky jakéhokoli typu.

> [!NOTE]
> Pro programy C++ by se namísto strukturovaného zpracování výjimek měla použít zpracování výjimek jazyka C++. Další informace naleznete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *Referenční příručce jazyka C++*.

Podívejte se na příklad [příkazu try-except](../c-language/try-except-statement-c.md) , abyste viděli, jak `try-finally` příkaz funguje.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[try-finally – příkaz](../cpp/try-finally-statement.md)
