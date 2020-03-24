---
title: Upozornění kompilátoru (úroveň 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 3fee3296eba4476680f4948b4a1f7fdee03e8840
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175204"
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
