---
title: Kompilátor upozornění (úroveň 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624013"
---
# <a name="compiler-warning-level-1-c4508"></a>Kompilátor upozornění (úroveň 1) C4508

'function': funkce by měla vracet hodnotu; 'void' předpokládá se návratový typ

Funkce nemá žádný návratový typ zadán. V takovém případě by měl také vyvolat C4430 a kompilátor implementuje opravu ohlášených C4430 (výchozí hodnota je int).

Pokud chcete vyřešit toto upozornění, explicitně deklarujte návratový typ funkce.

Následující ukázka generuje C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```