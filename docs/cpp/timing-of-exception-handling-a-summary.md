---
title: 'Načasování zpracování výjimky: Souhrn'
ms.date: 05/07/2019
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 3ed2e02412bd84663674a2df2c4454d21e83575a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188113"
---
# <a name="timing-of-exception-handling-a-summary"></a>Načasování zpracování výjimky: Souhrn

Obslužná rutina ukončení je prováděna bez ohledu na to, jak je ukončený blok příkazu **__try** . Mezi příčiny patří přechod z bloku **__try** , příkaz `longjmp`, který přenáší řízení z bloku a odvíjí od zpracování výjimek.

> [!NOTE]
>  Kompilátor společnosti C++ Microsoft podporuje dvě formy příkazů `setjmp` a `longjmp`. Rychlá verze obchází zpracování ukončení, ale je mnohem efektivnější. Chcete-li použít tuto verzi, zahrňte > souboru \<setjmp. h. Jiné verze podporují zpracování ukončení, jak je popsáno v předchozím odstavci. Chcete-li použít tuto verzi, zahrňte > souboru \<SETJMPEX. h. Zvýšení výkonu u rychlé verze závisí na konfiguraci hardwaru.

Operační systém spustí všechny obslužné rutiny ukončení ve správném pořadí, předtím než lze spustit jakýkoli jiný kód, včetně těla obslužné rutiny výjimky.

Je-li příčinou přerušení výjimka, systém musí před rozhodnutím, co ukončit, nejprve spustit část filtru jedné nebo více obslužných rutin výjimek. Pořadí událostí je následující:

1. Je vyvolána výjimka.

1. Systém v hierarchii vyhledá aktivní obslužné rutiny výjimek a spustí filtr obslužné rutiny s nejvyšší prioritou. To je obslužná rutina výjimky, která byla nainstalována jako poslední a je nejhlouběji vnořená, co se týče bloků a volání funkcí.

1. Pokud tento filtr předá řízení (vrátí hodnotu 0), proces pokračuje, dokud není nalezen filtr, který nepředá řízení.

1. Pokud tento filtr vrátí hodnotu-1, vykonání pokračuje v místě, kde byla výjimka vyvolána, a dojde k žádnému ukončení.

1. Jestliže filtr vrátí hodnotu 1, dojde k následujícím událostem:

   - Systém provede odvinutí zásobníku, zruší všechny rámce zásobníku mezi aktuálně prováděným kódem (kdy byla výjimka vyvolána) a rámcem zásobníku obsahujícím obslužnou rutinu výjimky, která převezme řízení.

   - Když je zásobník odvinut, je provedena každá obslužná rutina ukončení v zásobníku.

   - Je provedena samotná obslužná rutina výjimky.

   - Řízení přejde na řádek kódu na konci této obslužné rutiny výjimky.

## <a name="see-also"></a>Viz také

[Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
