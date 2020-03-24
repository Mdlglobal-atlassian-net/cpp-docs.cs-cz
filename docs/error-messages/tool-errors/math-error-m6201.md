---
title: Chyba matematické operace M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193703"
---
# <a name="math-error-m6201"></a>Chyba matematické operace M6201

' function ': Chyba _DOMAIN

Argument dané funkce byl mimo doménu platných vstupních hodnot pro danou funkci.

## <a name="example"></a>Příklad

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Tato chyba volá funkci `_matherr` s názvem funkce, jejími argumenty a typem chyby. Můžete přepsat funkci `_matherr` a přizpůsobit tak zpracování určitých matematických chyb s plovoucí desetinnou čárkou v době běhu.
