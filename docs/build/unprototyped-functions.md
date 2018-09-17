---
title: Neprototypové funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c030bd99fc185b3c52535aecb45697672ef4c14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717675"
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