---
title: Chyba kompilátoru C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: e3c37cba4b7df2df9e9784b3a1afb8dbf9c8e8d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491725"
---
# <a name="compiler-error-c3920"></a>Chyba kompilátoru C3920

' operator ": nejde definovat přírůstek a snížení přípony WinRT nebo volání příponový operátor CLR operátor WinRT nebo CLR bude volat odpovídající předpona WinRT nebo CLR – operátor (op_Increment/op_Decrement), ale s příponou sémantikou

Modul Windows Runtime a CLR nepodporují příponového operátoru a uživatelem definované Příponové operátory nejsou povoleny.  Můžete definovat operátor předpony a prefixový operátor se použije pro operace před a po přírůstku.

Následující ukázka generuje C3920 a ukazuje, jak ho opravit:

```
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