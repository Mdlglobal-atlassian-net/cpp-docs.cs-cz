---
title: Kompilátor upozornění (úroveň 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574262"
---
# <a name="compiler-warning-level-1-c4612"></a>Kompilátor upozornění (úroveň 1) C4612

> Chyba v názvu vloženého souboru

## <a name="remarks"></a>Poznámky

Toto upozornění se zobrazí s **#pragma include_alias** kdy název souboru je nesprávný nebo chybí.

Argumenty, které mají **#pragma include_alias** příkaz můžete použít formuláře uvozovky ("*název souboru*") nebo forma lomené závorky (\<*filename*>), ale obě musí pomocí stejného formuláře.

## <a name="example"></a>Příklad

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```