---
title: Chyba kompilátoru C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759643"
---
# <a name="compiler-error-c2743"></a>Chyba kompilátoru C2743

Type: nejde zachytit nativní typ s __clrcall destruktorem nebo kopírovacím konstruktorem.

Modul kompilovaný pomocí **/CLR** se pokusil zachytit výjimku z nativního typu a kde destruktor nebo kopírovací konstruktor typu používá konvenci volání `__clrcall`.

Při kompilaci s možností **/CLR**očekává zpracování výjimek členské funkce v nativním typu [__cdecl](../../cpp/cdecl.md) a nikoli [__clrcall](../../cpp/clrcall.md). Nativní typy s členskými funkcemi pomocí `__clrcall` konvence volání nelze zachytit v modulu zkompilovaném pomocí **/CLR**.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2743.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
