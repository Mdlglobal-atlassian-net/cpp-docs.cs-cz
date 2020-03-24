---
title: Upozornění linkerů LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183355"
---
# <a name="linker-tools-warning-lnk4092"></a>Upozornění linkerů LNK4092

oddíl s možností zápisu oddílu obsahuje přemístění. Image možná nebude správně fungovat.

Linker vygeneruje toto upozornění vždy, když máte sdílený oddíl, který vás upozorní na potenciálně vážný problém.

Jedním ze způsobů, jak sdílet data mezi více procesy, je označit oddíl jako "Shared". Označení oddílu jako sdíleného může ale způsobit problémy. Máte například knihovnu DLL, která obsahuje deklarace, jako je to v části sdílená data:

```
int var = 1;
int *pvar = &var;
```

Linker nemůže vyřešit `pvar`, protože jeho hodnota závisí na tom, kde je knihovna DLL načtena v paměti, takže v knihovně DLL vloží záznam o přemístění. Když je knihovna DLL načtena do paměti, adresa `var` může být vyřešena a `pvar` přiřazena. Pokud jiný proces načte stejnou knihovnu DLL, ale nemůže ji načíst na stejné adrese, přemístění pro adresu `var` bude aktualizováno pro druhý proces a adresní prostor prvního procesu bude ukazovat na špatnou adresu.
