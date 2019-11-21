---
title: 'Timing of exception handling: A summary'
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
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246335"
---
# <a name="timing-of-exception-handling-a-summary"></a>Timing of exception handling: A summary

A termination handler is executed no matter how the **__try** statement block is terminated. Causes include jumping out of the **__try** block, a `longjmp` statement that transfers control out of the block, and unwinding the stack due to exception handling.

> [!NOTE]
>  The Microsoft C++ compiler supports two forms of the `setjmp` and `longjmp` statements. Rychlá verze obchází zpracování ukončení, ale je mnohem efektivnější. To use this version, include the file \<setjmp.h>. Jiné verze podporují zpracování ukončení, jak je popsáno v předchozím odstavci. To use this version, include the file \<setjmpex.h>. Zvýšení výkonu u rychlé verze závisí na konfiguraci hardwaru.

Operační systém spustí všechny obslužné rutiny ukončení ve správném pořadí, předtím než lze spustit jakýkoli jiný kód, včetně těla obslužné rutiny výjimky.

Je-li příčinou přerušení výjimka, systém musí před rozhodnutím, co ukončit, nejprve spustit část filtru jedné nebo více obslužných rutin výjimek. Pořadí událostí je následující:

1. Je vyvolána výjimka.

1. Systém v hierarchii vyhledá aktivní obslužné rutiny výjimek a spustí filtr obslužné rutiny s nejvyšší prioritou. To je obslužná rutina výjimky, která byla nainstalována jako poslední a je nejhlouběji vnořená, co se týče bloků a volání funkcí.

1. Pokud tento filtr předá řízení (vrátí hodnotu 0), proces pokračuje, dokud není nalezen filtr, který nepředá řízení.

1. If this filter returns -1, execution continues where the exception was raised, and no termination takes place.

1. Jestliže filtr vrátí hodnotu 1, dojde k následujícím událostem:

   - Systém provede odvinutí zásobníku, zruší všechny rámce zásobníku mezi aktuálně prováděným kódem (kdy byla výjimka vyvolána) a rámcem zásobníku obsahujícím obslužnou rutinu výjimky, která převezme řízení.

   - Když je zásobník odvinut, je provedena každá obslužná rutina ukončení v zásobníku.

   - Je provedena samotná obslužná rutina výjimky.

   - Řízení přejde na řádek kódu na konci této obslužné rutiny výjimky.

## <a name="see-also"></a>Viz také:

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)