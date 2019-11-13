---
title: Upozornění kompilátoru (úroveň 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 394a59a472100cc30476b5bb87f30c45d867f94b
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966294"
---
# <a name="compiler-warning-level-1-c4508"></a>Upozornění kompilátoru (úroveň 1) C4508

' function ': funkce by měla vracet hodnotu; Předpokládá se návratový typ void.

Funkce nemá zadaný žádný návratový typ. V tomto případě by měl být C4430 také požár a kompilátor implementuje opravu oznámenou C4430 (výchozí hodnota je int).

Chcete-li vyřešit toto upozornění, explicitně deklarujte návratový typ funkcí.

Následující ukázka generuje C4508:

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```