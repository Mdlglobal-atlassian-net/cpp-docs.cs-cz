---
title: Upozornění (úroveň 1) C4722 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4722
dev_langs:
- C++
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f450120ff05c7e13888bf4b4ce4425405525b4c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112496"
---
# <a name="compiler-warning-level-1-c4722"></a>Kompilátor upozornění (úroveň 1) C4722

'function': destruktor nikdy nevrací potenciální nevrácená paměť

Tok řízení ukončí v destruktoru. Vlákno nebo celý program se ukončí a nemusí být všeobecně dostupné přidělené prostředky.  Kromě toho pokud destruktor bude zavolána pro uvolnění zásobníku během zpracování výjimek, chování spustitelný soubor není definováno.

Pokud chcete vyřešit, odeberte volání funkce, které způsobí, že destruktor není vrátit.

## <a name="example"></a>Příklad

Následující ukázka generuje C4722:

```
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```