---
title: Upozornění (úroveň 4) C4460 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4460
dev_langs:
- C++
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2635090d5aea4d5b80632ddf84b0eb3d2ccbdb6f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021288"
---
# <a name="compiler-warning-level-4-c4460"></a>Kompilátor upozornění (úroveň 4) C4460

WinRT nebo CLR operátor 'operator', má parametr předaný odkazem. WinRT nebo CLR operátor 'operator' má odlišnou sémantiku než operátor C++ 'operator', nechtěli jste předat hodnotu?

Hodnota se předá odkazem na uživatelské prostředí Windows Runtime nebo CLR operátor. Pokud se hodnota změní uvnitř funkce, mějte na paměti, že vrácená hodnota po volání funkce se přiřadí návratová hodnota funkce. Ve standardním jazyce C++ změněné hodnoty se projeví po volání funkce.

## <a name="example"></a>Příklad

Následující ukázka generuje C4460 a ukazuje, jak ho opravit.

```
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