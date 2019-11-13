---
title: Upozornění kompilátoru (úroveň 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 85921d67b764a28f9251f0c8b6e3fc807edd0f5b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052456"
---
# <a name="compiler-warning-level-1-c4722"></a>Upozornění kompilátoru (úroveň 1) C4722

' function ': destruktor se nikdy nevrátí, potenciální nevrácená paměť

Tok řízení končí v destruktoru. Vlákno nebo celý program budou ukončeny a přidělené prostředky nemusí být uvolněny.  Kromě toho, pokud bude destruktor volán pro odvinutí zásobníku během zpracování výjimky, chování spustitelného souboru není definováno.

Chcete-li řešení vyřešit, odeberte volání funkce, které způsobí, že se destruktor nevrátí.

## <a name="example"></a>Příklad

Následující ukázka generuje C4722:

```cpp
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