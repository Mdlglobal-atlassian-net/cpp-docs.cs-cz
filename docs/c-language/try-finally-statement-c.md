---
title: try-finally – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 82cc5ffa3f50196fc5f518b8bb5b2080ff14fd8d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151829"
---
# <a name="try-finally-statement-c"></a>try-finally – příkaz (C)

**Microsoft Specific**

`try-finally` Příkaz je rozšířením společnosti Microsoft pro jazyk C, která umožňuje aplikacím zaručit spuštění kódu čištění, když dojde k přerušení vykonání bloku kódu. Čištění se skládá z úlohy, jako jsou rušení přidělení paměti, zavírání souborů a uvolněním popisovačů souborů. `try-finally` Příkaz je užitečné hlavně pro rutiny, které mají několika místech, kde se provede kontrola pro chybu, která by mohla způsobit předčasné vrátit z rutiny.

*try-finally-statement*: **__try**  *compound-statement* 

**__finally**  *compound-statement* 

Složený příkaz za `__try` klauzule je chráněná část. Složený příkaz za `__finally` klauzule je obslužná rutina ukončení. Obslužná rutina udává sadu akcí, které jsou spuštěny při chráněná část je byl ukončen, zda je chráněná část ukončil výjimku (abnormální ukončení) nebo standardní fall prostřednictvím (normální ukončení).

Ovládací prvek dosáhne `__try` prohlášení jednoduchý sekvenční provádění (fall prostřednictvím). Když přejde do ovládacího prvku `__try` prohlášení, jeho přidružená obslužná rutina stane aktivním. Spuštění probíhá následujícím způsobem:

1. Chráněná část je spuštěna.

1. Je vyvolána obslužná rutina ukončení.

1. Po dokončení obslužné rutiny ukončení provádění pokračuje `__finally` příkazu. Bez ohledu na to, jak chráněné části zakončení (například prostřednictvím `goto` příkazu mimo chráněné text nebo prostřednictvím `return` příkaz), obslužné rutiny ukončení je spuštěn před tok řízení přesune mimo chráněnou část.

`__leave` – Klíčové slovo je platný v rámci `try-finally` blok příkazů. Účinek `__leave` je přechod na konci `try-finally` bloku. Obslužná rutina ukončení se okamžitě spustí. I když `goto` příkaz můžete použít k dosažení stejného výsledku `goto` příkaz způsobí, že odvíjení zásobníku. `__leave` Příkaz je mnohem efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení `try-finally` pomocí příkazu `return` příkazu nebo `longjmp` funkci run-time je považován za abnormální ukončení. Není povoleno přejít do `__try` příkazu, ale právní přejít mimo něj. Všechny `__finally` příkazy, které jsou aktivní mezi bodem odeslání a cíl musí být spuštěn. To se označuje jako "místní uvolnění."

Obslužné rutiny ukončení není volána, pokud proces je ukončen při provádění `try-finally` příkazu.

> [!NOTE]
>  Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Mechanismus zpracování výjimek jazyka C++ je také mnohem více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu.

> [!NOTE]
>  Pro programy v jazyce C++ je třeba použít zpracování výjimek jazyka C++ místo strukturované zpracování výjimek. Další informace najdete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *referenční dokumentace jazyka C++*.

Podívejte se na příklad pro [zkuste-except – příkaz](../c-language/try-except-statement-c.md) zobrazíte jak `try-finally` příkaz funguje.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[try-finally – příkaz](../cpp/try-finally-statement.md)
