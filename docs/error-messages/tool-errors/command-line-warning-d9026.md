---
title: Upozornění příkazového řádku D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214204"
---
# <a name="command-line-warning-d9026"></a>Upozornění příkazového řádku D9026

možnosti platí pro celý příkazový řádek.

Možnost zadaná v příkazu po byl zadán název souboru. Možnost byla použita k souboru, který ním.

Například v příkazu

```
CL verdi.c /G5 puccini.c
```

soubor VERDI.c bude zkompilován pomocí možnosti /G5, nikoli ve výchozím /G4.

Toto chování se liší od některých předchozích verzí, které platí pouze pro kompilaci pomocí volby zadané před název souboru, což vede k VERDI.c/G4 a PUCCINI.c kompilovaná pomocí /G5.