---
title: Chyba kompilátoru C3920 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b85638907f350eb3545a858f1319e56b2459f09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112704"
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