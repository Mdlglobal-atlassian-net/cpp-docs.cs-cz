---
title: Omezení obslužných rutin ukončení
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179065"
---
# <a name="restrictions-on-termination-handlers"></a>Omezení obslužných rutin ukončení

Pomocí příkazu **goto** nelze přejít do bloku příkazu **__try** nebo do bloku příkazu **__finally** . Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. (Můžete však přejít z bloku příkazu **__try** .) Nemůžete také vnořit obslužnou rutinu výjimky nebo obslužné rutiny ukončení uvnitř bloku **__finally** .

Kromě toho některé druhy kódu, které jsou povoleny v obslužné rutině ukončení, vyvolávají problematické výsledky, takže je byste měli použít s opatrností, pokud vůbec. Jedním z nich je příkaz **goto** , který přeskočí z bloku příkazu **__finally** . Pokud je blok spuštěn jako součást normálního ukončení, nedošlo k žádné neobvyklé situaci. Pokud však systém odvíjí od zásobníku, toto zrušení se zastaví a aktuální funkce získá řízení, jako kdyby nedocházelo k abnormálnímu ukončení.

Příkaz **return** v bloku příkazu **__finally** prezentuje zhruba stejnou situaci. Řízení se vrátí bezprostřednímu volajícímu funkce obsahující obslužnou rutinu ukončení. Pokud systém odvíjí zásobník, tento proces je zastaven a program pokračuje, jako kdyby nebyla vyvolána žádná výjimka.

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
