---
title: Upozornění kompilátoru (úroveň 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186969"
---
# <a name="compiler-warning-level-1-c4382"></a>Upozornění kompilátoru (úroveň 1) C4382

> *typ*vyvolání: typ s __clrcall destruktorem nebo kopírovacím konstruktorem se dá zachytit jedině v modulu/CLR: Pure.

## <a name="remarks"></a>Poznámky

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

Při kompilaci s možností **/CLR** (ne **/clr: Pure**) očekává zpracování výjimek členské funkce v nativním typu [__cdecl](../../cpp/cdecl.md) a nikoli [__clrcall](../../cpp/clrcall.md). Nativní typy s členskými funkcemi pomocí `__clrcall` konvence volání nelze zachytit v modulu zkompilovaném pomocí **/CLR**.

Pokud bude výjimka zachycena v modulu zkompilovaném pomocí **/clr: Pure**, můžete toto upozornění ignorovat.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

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
