---
title: Upozornění kompilátoru (úroveň 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: 7f394af9dc0362035b9361981fdca077a3a915d5
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682923"
---
# <a name="compiler-warning-level-4-c4460"></a>Upozornění kompilátoru (úroveň 4) C4460

Operátor WinRT nebo CLR ' operator ', má parametr předaný odkazem. Operátor WinRT nebo CLR ' operator ' má odlišnou sémantiku C++ z operátoru ' operator ', kterou jste chtěli předat hodnotou?

Předala se hodnota odkazem na uživatelsky definovaný prostředí Windows Runtime nebo operátor CLR. Pokud je hodnota ve funkci změněna, Všimněte si, že hodnota vrácená po volání funkce bude přiřazena návratovou hodnotu funkce. Ve standardu C++se změněná hodnota projeví po volání funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C4460 a ukazuje, jak ji opravit.

```cpp
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```