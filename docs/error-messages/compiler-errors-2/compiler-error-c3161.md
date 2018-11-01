---
title: Chyba kompilátoru C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501657"
---
# <a name="compiler-error-c3161"></a>Chyba kompilátoru C3161

'rozhraní': vnoření třídy, struktury, sjednocení nebo rozhraní v rozhraní je neplatný; vnoření rozhraní ve třídě, struktury nebo sjednocení je neplatný

[__Interface](../../cpp/interface.md) může být použit pouze v globálním oboru nebo v oboru názvů. Třída, struktura nebo sjednocení nemůže objevit v rozhraní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```