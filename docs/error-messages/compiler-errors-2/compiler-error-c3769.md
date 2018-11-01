---
title: Chyba kompilátoru C3769
ms.date: 11/04/2016
f1_keywords:
- C3769
helpviewer_keywords:
- C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
ms.openlocfilehash: 68845b446541b8d76ebd2b873a34b7e32ef314e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480350"
---
# <a name="compiler-error-c3769"></a>Chyba kompilátoru C3769

'type': vnořená třída nemůže mít stejný název jako okamžitě nadřazené třídy

Vnořená třída nemůže mít stejný název jako okamžitě nadřazené třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C3769.

```
// C3769.cpp
// compile with: /c
class x {
   class x {};   // C3769
   class y {
      class x{};   // OK
   };
};
```