---
title: Kompilátor upozornění (úroveň 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390487"
---
# <a name="compiler-warning-level-1-c4382"></a>Kompilátor upozornění (úroveň 1) C4382

> vyvolání "*typ*': typ s destruktorem __clrcall nebo kopírovacím konstuktorem se dá zachytit jedině v/CLR: pure modulu

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Při kompilaci s **/CLR** (ne **/CLR: pure**), zpracování výjimek v nativním typu bude očekává členské funkce [__cdecl](../../cpp/cdecl.md) a ne [__clrcall](../../cpp/clrcall.md). Nativní typy pomocí členské funkce pomocí `__clrcall` konvence volání nemůže být zachycena v modul zkompilovaný pomocí **/CLR**.

Pokud výjimka bude zachycena v modul zkompilovaný pomocí **/CLR: pure**, můžete toto upozornění ignorovat.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```