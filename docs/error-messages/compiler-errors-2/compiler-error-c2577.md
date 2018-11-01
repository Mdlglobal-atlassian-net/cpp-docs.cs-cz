---
title: Chyba kompilátoru C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 4406aa90b26bc517308132ae9cccd003d44a9aad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530543"
---
# <a name="compiler-error-c2577"></a>Chyba kompilátoru C2577

'member': destruktor nebo finalizační metoda nemůže mít návratový typ.

Destruktor nebo finalizační metoda nemůže vrátit hodnotu `void` nebo jakéhokoli jiného typu. Odeberte `return` příkaz z definice destruktor.

## <a name="example"></a>Příklad

Následující ukázka generuje C2577.

```
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```