---
title: Chyba kompilátoru C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: 416752054f7397a058329e1ee4bdaef693dd0d28
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758460"
---
# <a name="compiler-error-c3920"></a>Chyba kompilátoru C3920

' operator ': nelze definovat prefixový přírůstek/snižovat WinRT nebo operátor CLR volání přípony WinRT nebo operátoru CLR zavolá odpovídající předponu WinRT nebo CLR (op_Increment/op_Decrement), ale se sémantikou přípony

Prostředí Windows Runtime a CLR nepodporují operátor přípon a uživatelsky definované operátory přípon nejsou povoleny.  Můžete definovat operátor předpony a operátor předpony bude použit pro operace před i po zvýšení hodnoty.

Následující ukázka generuje C3920 a ukazuje, jak ji opravit:

```cpp
// C3920.cpp
// compile with: /clr /LD
public value struct V {
   static V operator ++(V me, int)
   // try the following line instead
   // static V operator ++(V me)
   {   // C3920
      me.m_i++;
      return me;
   }

   int m_i;
};
```
