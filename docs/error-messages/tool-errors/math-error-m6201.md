---
title: Chyba matematické operace M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393243"
---
# <a name="math-error-m6201"></a>Chyba matematické operace M6201

'function': Chyba _domény

Argument pro danou funkci bylo mimo doménu platné vstupní hodnoty pro tuto funkci.

## <a name="example"></a>Příklad

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Tato chyba volání `_matherr` funkce s názvem funkce, argumentů a typ chyby. Je možné přepsat `_matherr` přizpůsobit zpracování některých chyb za běhu s plovoucí desetinnou čárkou matematické funkce.