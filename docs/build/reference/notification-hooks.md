---
title: Háky oznámení
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, notification hooks
ms.assetid: e9c291ed-2f2d-4319-a171-09800625256f
ms.openlocfilehash: 884d8e8479b7cad28d99e19adfac4d05dbeec5f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818307"
---
# <a name="notification-hooks"></a>Háky oznámení

Háky oznámení se nazývají těsně před plánovaným v pomocné rutině budou provedeny následující akce:

- Uložené popisovač do knihovny je zaškrtnuté políčko, pokud chcete zobrazit, pokud již byl načten.

- **LoadLibrary** nazývá pokusu o načtení knihovny DLL.

- **GetProcAddress** voláním se pokusí získat adresu procedury.

- Vraťte se na import odloženého načtení převodní rutina.

Je povolené hook oznámení:

- Zadáním novou definici ukazatele **__pfnDliNotifyHook2** , který je inicializován tak, aby odkazoval na vlastní funkce, která bude přijímat oznámení.

   \-or-

- Tím, že nastavíte ukazatel **__pfnDliNotifyHook2** do funkce háku před všechna volání do knihovny DLL, která je program zpozdit načtení.

Pokud je oznámení **dliStartProcessing**, funkce háku může vrátit:

- NULL

   Pomocná rutina výchozí zpracovává načítání knihovny DLL. To je užitečné, která se má volat pouze k informačním účelům.

- Ukazatel na funkci

   Počet zpracování odloženě zaváděné výchozí. To umožňuje zadat vlastní obslužnou rutinu zatížení.

Pokud je oznámení **dliNotePreLoadLibrary**, funkce háku může vrátit:

- 0, pokud chce jenom informativní oznámení.

- HMODULE načtené knihovny DLL, pokud ji načíst samotná knihovna DLL.

Pokud je oznámení **dliNotePreGetProcAddress**, funkce háku může vrátit:

- 0, pokud chce jenom informativní oznámení.

- Adresa importované funkce, je-li funkce háku získá samotnou adresu.

Pokud je oznámení **dliNoteEndProcessing**, návratová hodnota funkce háku je ignorována.

Pokud tento ukazatel se inicializuje (nenulový), pomocné rutiny zatížení zpoždění vyvolá funkci v určitých bodech oznámení v průběhu jeho spuštění. Ukazatel na funkci obsahuje následující definice:

```C
// The "notify hook" gets called for every call to the
// delay load helper.  This allows a user to hook every call and
// skip the delay load helper entirely.
//
// dliNotify == {
//  dliStartProcessing |
//  dliNotePreLoadLibrary  |
//  dliNotePreGetProc |
//  dliNoteEndProcessing}
//  on this call.
//
ExternC
PfnDliHook   __pfnDliNotifyHook2;

// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

Oznámení předat **DelayLoadInfo** Struktura funkce háku spolu s hodnotou oznámení. Tato data jsou stejné jako, který používá pomocná rutina zatížení zpoždění. Hodnota oznámení bude jedna z hodnot fronty definovaných v [struktura a definice konstant](structure-and-constant-definitions.md).

## <a name="see-also"></a>Viz také:

[Zpracování chyb a oznámení](error-handling-and-notification.md)
