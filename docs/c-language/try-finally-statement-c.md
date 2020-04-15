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

Příkaz `try-finally` je rozšíření společnosti Microsoft k jazyku C, který umožňuje aplikacím zaručit spuštění kódu vyčištění při přerušení provádění bloku kódu. Vyčištění se skládá z takových úkolů, jako je zrušení přidělení paměti, zavření souborů a uvolnění popisovačů souborů. Příkaz `try-finally` je zvláště užitečné pro rutiny, které mají několik míst, kde je provedena kontrola pro chybu, která by mohla způsobit předčasný návrat z rutiny.

*try-finally-statement*: **__try**  *složený příkaz*

**__finally**  *složený příkaz*

Složený příkaz za `__try` klauzulí je střežené části. Složený příkaz po `__finally` klauzuli je obslužná rutina ukončení. Obslužná rutina určuje sadu akcí, které se provádějí při ukončení střežené části, zda je chráněná část ukončena výjimkou (abnormální ukončení) nebo standardním propadnením (normální ukončení).

Ovládací prvek `__try` dosáhne příkazu jednoduchým sekvenčním prováděním (propadne). Když ovládací prvek `__try` zadá příkaz, jeho přidružená obslužná rutina se stane aktivní. Exekuce probíhá takto:

1. Chráněná část je spuštěna.

1. Obslužná rutina ukončení je vyvolána.

1. Po dokončení obslužné rutiny ukončení, provádění pokračuje po příkazu. `__finally` Bez ohledu na to, jak chráněná část `goto` končí (například prostřednictvím `return` příkazu z hlísty z hlísty nebo prostřednictvím příkazu), je obslužná rutina ukončení provedena před tím, než se tok řízení přesune z hlídané části.

Klíčové `__leave` slovo je `try-finally` platné v rámci bloku příkazu. Efekt `__leave` je skočit na konec `try-finally` bloku. Obslužná rutina ukončení je okamžitě spuštěna. Přestože `goto` příkaz lze použít k dosažení `goto` stejného výsledku, příkaz způsobí, že unwinding zásobníku. Příkaz `__leave` je efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení příkazu `try-finally` pomocí `return` příkazu `longjmp` nebo funkce run-time je považováno za abnormální ukončení. Je nezákonné skočit do `__try` prohlášení, ale legální skočit z jednoho. Všechny `__finally` příkazy, které jsou aktivní mezi výchozím bodem a cílem, musí být spuštěny. Tomu se říká "místní odpočinek".

Obslužná rutina ukončení není volána, pokud je proces zabit při provádění příkazu. `try-finally`

> [!NOTE]
> Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Také mechanismus zpracování výjimek Jazyka C++ je mnohem flexibilnější v tom, že může zpracovávat výjimky libovolného typu.

> [!NOTE]
> Pro programy jazyka C++ by mělo být místo strukturovaného zpracování výjimek použito zpracování výjimek jazyka C++. For more information, see [Exception Handling](../cpp/exception-handling-in-visual-cpp.md) in the *C++ Language Reference*.

Podívejte se na příklad pro [try-except prohlášení](../c-language/try-except-statement-c.md) zobrazíte, `try-finally` jak příkaz funguje.

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[try-finally prohlášení](../cpp/try-finally-statement.md)
