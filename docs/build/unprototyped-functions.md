---
title: Neprototypové funkce
ms.date: 11/04/2016
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
ms.openlocfilehash: 38207be6111dadc338593e55b683b88e0480e1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633425"
---
# <a name="unprototyped-functions"></a>Neprototypové funkce

Pro funkce nelze používat plně prototypované volající předá celočíselné hodnoty jako celá čísla a hodnoty s plovoucí desetinnou čárkou jako dvojitou přesností. Pouze hodnoty s plovoucí desetinnou čárkou registru celých čísel a registr s plovoucí desetinnou čárkou obsahovat hodnoty typu float v případě, že volaný očekává, že hodnota v registrech celé číslo.

```
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)