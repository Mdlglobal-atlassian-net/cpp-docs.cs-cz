---
title: FpCsr
ms.date: 11/04/2016
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
ms.openlocfilehash: 018ce39a194d5153f73fa452990844362190e6bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472813"
---
# <a name="fpcsr"></a>FpCsr

Stav registrace obsahuje také x87 FPU řídicího slova. Určuje konvenci volání tento registr stálé.

X87 FPU kontrolní slovo registru je nastavena na následující standardní hodnoty na začátku provádění programu:

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

Volaný, který upravuje některé z polí v rámci FPCSR musí obnovit před vrácením volající funkci. Kromě toho volající, který změní některé z těchto polí musí obnovit na standardní hodnoty před vyvoláním volaného Pokud smlouvou volaný očekává, že změněné hodnoty.

Existují dvě výjimky k pravidlům týkající se jiných volatility příznaky ovládacích prvků:

1. Ve funkcích, kde zdokumentovaných účel danou funkci stálé FpCsr příznaků.

1. Pokud je prokazatelně správné, že porušení pravidla výsledky v programech, které se chová/znamená, že stejně jako program, ve kterém nejsou porušena tato pravidla, například prostřednictvím analýzy celého programu.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)