---
title: C3920 Chyba kompilátoru | Microsoft Docs
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
ms.openlocfilehash: 6ced0a0f8fa2b6694de4dd901d71f6721e12493b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3920"></a>C3920 chyby kompilátoru
' operátor '': nelze definovat operátory přírůstek nebo snížení WinRT nebo CLR operátor volání operátory operátor WinRT nebo CLR bude volat předponu odpovídající WinRT nebo CLR – operátor (op_Increment op_Decrement), ale s sémantiku operátory  
  
 Prostředí Windows Runtime a CLR nepodporují operátor operátory a operátory uživatelem definované operátory nejsou povoleny.  Můžete definovat předponu operátor a operátor předpona se použije pro operace před a po přírůstku.  
  
 Následující ukázka generuje C3920 a ukazuje, jak to opravit:  
  
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