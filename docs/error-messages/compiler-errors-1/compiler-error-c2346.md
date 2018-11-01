---
title: Chyba kompilátoru C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527358"
---
# <a name="compiler-error-c2346"></a>Chyba kompilátoru C2346

'function' nedá zkompilovat jako nativní: důvod

Kompilátor se nepodařilo zkompilovat funkci do jazyka MSIL.

Další informace najdete v tématu [spravované, nespravované](../../preprocessor/managed-unmanaged.md) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Odeberte kód ve funkci nejde zkompilovat do jazyka MSIL.

1. Buď se nekompilují modul s parametrem **/CLR**, nebo označit funkce jako nespravované s unmanaged – Direktiva pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C2346.

```
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