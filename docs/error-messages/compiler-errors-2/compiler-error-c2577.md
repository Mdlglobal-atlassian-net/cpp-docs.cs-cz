---
title: Chyba kompilátoru C2577 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2577
dev_langs:
- C++
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d9a2b09fc9b8b15c4fc21f5eb537f18f5d3b03e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065813"
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