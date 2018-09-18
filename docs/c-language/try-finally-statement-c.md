---
title: try-finally Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2273d67ef2e187d47ea3df066620ae7a3895ec4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060951"
---
# <a name="try-finally-statement-c"></a>try-finally – příkaz (C)

**Specifické pro Microsoft**

`try-finally` Příkaz je rozšířením společnosti Microsoft pro jazyk C, která umožňuje aplikacím zaručit spuštění kódu čištění, když dojde k přerušení vykonání bloku kódu. Čištění se skládá z úlohy, jako jsou rušení přidělení paměti, zavírání souborů a uvolněním popisovačů souborů. `try-finally` Příkaz je užitečné hlavně pro rutiny, které mají několika místech, kde se provede kontrola pro chybu, která by mohla způsobit předčasné vrátit z rutiny.

*try-finally-statement*: **__try***compound-statement* 

**__finally***compound-statement* 

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

## <a name="see-also"></a>Viz také

[try-finally – příkaz](../cpp/try-finally-statement.md)