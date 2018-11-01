---
title: Kompilátor upozornění (úroveň 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5ec0aea543053d699db7483df7dd7ea91b3af715
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594542"
---
# <a name="compiler-warning-level-1-c4716"></a>Kompilátor upozornění (úroveň 1) C4716

'function' musí vracet hodnotu

Dané funkce nevrací hodnotu.

Pouze funkce s návratovým typem void lze použít příkaz return bez doprovodné návratové hodnoty.

Nedefinovaná hodnota se vrátí při volání této funkce.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md).

Následující ukázka generuje C4716:

```
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```