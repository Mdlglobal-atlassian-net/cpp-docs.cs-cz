---
title: Upozornění příkazového řádku D9026 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07be633e56dad6c8f0b304a3c88c1b9919221d4a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079151"
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