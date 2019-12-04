---
title: Chyba kompilátoru C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: fc2aeac02ecc3f29406c2288051ca6cd9d3a4923
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760007"
---
# <a name="compiler-error-c2346"></a>Chyba kompilátoru C2346

funkci Function nejde zkompilovat jako nativní: důvod.

Kompilátor nemohl kompilovat funkci do jazyka MSIL.

Další informace naleznete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md) a [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Odeberte kód ve funkci, která nemůže být zkompilována do jazyka MSIL.

1. Buď nezkompilujte modul s **/CLR**, nebo označte funkci jako nespravovanou pomocí nespravované direktivy pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C2346.

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```
