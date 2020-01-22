---
title: Chyba kompilátoru C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: 91f2bac38166a8972193a7aaa7e84913b941c799
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518319"
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

int main()
{
   S s;
}
```
