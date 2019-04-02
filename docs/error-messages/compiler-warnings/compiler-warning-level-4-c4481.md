---
title: Kompilátor upozornění (úroveň 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: fe96ff50f4081e3c9dbe3c7eb68da156a69c96ab
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776359"
---
# <a name="compiler-warning-level-4-c4481"></a>Kompilátor upozornění (úroveň 4) C4481

používá se nestandardní rozšíření: specifikátor '– klíčové slovo' override

Klíčové slovo se použil, který není standardu jazyka C++, například jeden specifikátory přepsání, které také funguje pod parametrem/CLR.  Další informace najdete v tématu,

- [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Override – specifikátory](../../extensions/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Příklad

Následující ukázka generuje C4481.

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```