---
title: Kompilátor upozornění (úroveň 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 320061c2daf2be042afe45828af637638399beaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469469"
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