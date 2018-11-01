---
title: Chyba kompilátoru C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 03cd7c13e093be5073b3df7e7cf29dda870bc47a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530995"
---
# <a name="compiler-error-c2743"></a>Chyba kompilátoru C2743

'type': nelze zachytit nativní typ s destruktorem __clrcall nebo kopírovacím konstuktorem

Modul zkompilovaný s **/CLR** došlo k pokusu o zachytit výjimku nativní typ a kde typu destruktor nebo kopírovací konstuktor používá `__clrcall` konvence volání.

Při kompilaci s **/CLR**, zpracování výjimek očekává, že členské funkce v nativním typu bude [__cdecl](../../cpp/cdecl.md) a ne [__clrcall](../../cpp/clrcall.md). Nativní typy pomocí členské funkce pomocí `__clrcall` konvence volání nemůže být zachycena v modul zkompilovaný pomocí **/CLR**.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2743.

```
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