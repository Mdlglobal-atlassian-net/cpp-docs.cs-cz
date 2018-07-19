---
title: 'Načasování zpracování výjimky: Souhrn | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2ac5abb13ae700e464635efc90a91c4a5835ab
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939413"
---
# <a name="timing-of-exception-handling-a-summary"></a>Načasování zpracování výjimky: souhrn
Obslužné rutiny ukončení provádí bez ohledu na to, jak **__try** se ukončí blok příkazů. Příčiny opuštění **__try** bloku, `longjmp` příkaz, který opuštění bloku a odvíjení zásobníku z důvodu zpracování výjimek.  
  
> [!NOTE]
>  Jazyk Visual C++ podporuje dva tvary příkazů `setjmp` a `longjmp`. Rychlá verze obchází zpracování ukončení, ale je mnohem efektivnější. Chcete-li tuto verzi použít, zahrňte soubor \<setjmp.h >. Jiné verze podporují zpracování ukončení, jak je popsáno v předchozím odstavci. Chcete-li tuto verzi použít, zahrňte soubor \<setjmpex.h >. Zvýšení výkonu u rychlé verze závisí na konfiguraci hardwaru.  
  
 Operační systém spustí všechny obslužné rutiny ukončení ve správném pořadí, předtím než lze spustit jakýkoli jiný kód, včetně těla obslužné rutiny výjimky.  
  
 Je-li příčinou přerušení výjimka, systém musí před rozhodnutím, co ukončit, nejprve spustit část filtru jedné nebo více obslužných rutin výjimek. Pořadí událostí je následující:  
  
1.  Je vyvolána výjimka.  
  
2.  Systém v hierarchii vyhledá aktivní obslužné rutiny výjimek a spustí filtr obslužné rutiny s nejvyšší prioritou. To je obslužná rutina výjimky, která byla nainstalována jako poslední a je nejhlouběji vnořená, co se týče bloků a volání funkcí.  
  
3.  Pokud tento filtr předá řízení (vrátí hodnotu 0), proces pokračuje, dokud není nalezen filtr, který nepředá řízení.  
  
4.  Pokud tento filtr vrátí hodnotu -1, provádění pokračuje, kde byla výjimka vyvolána, a nedojde k žádnému ukončení probíhá.  
  
5.  Jestliže filtr vrátí hodnotu 1, dojde k následujícím událostem:  
  
    -   Systém provede odvinutí zásobníku, zruší všechny rámce zásobníku mezi aktuálně prováděným kódem (kdy byla výjimka vyvolána) a rámcem zásobníku obsahujícím obslužnou rutinu výjimky, která převezme řízení.  
  
    -   Když je zásobník odvinut, je provedena každá obslužná rutina ukončení v zásobníku.  
  
    -   Je provedena samotná obslužná rutina výjimky.  
  
    -   Řízení přejde na řádek kódu na konci této obslužné rutiny výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)