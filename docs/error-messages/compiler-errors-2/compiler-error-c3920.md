---
title: Chyba kompilátoru C3920
ms.date: 11/04/2016
f1_keywords:
- C3920
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
ms.openlocfilehash: d7163cf07a440a0afd1216b3e5cf665326ffb963
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522100"
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