---
title: Kompilátoru (úroveň 1) upozornění C4929 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4929
dev_langs:
- C++
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e862a13059a8fc20513a6d79dcd3282e66ce0814
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301841"
---
# <a name="compiler-warning-level-1-c4929"></a>C4929 kompilátoru upozornění (úroveň 1)
'file': knihovny typů obsahuje sjednocení; ignoruje kvalifikátor 'embedded_idl –.  
  
 Embedded_idl – atribut [#import](../../preprocessor/hash-import-directive-cpp.md) nebylo možné aplikovat knihovny typů, protože se nachází v knihovně typ spojení. Chcete-li vyřešit toto upozornění, nepoužívejte embedded_idl –.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje komponentu.  
  
```  
// C4929a.cpp  
// compile with: /LD /link /TLBOUT:C4929a.tlb  
#include <objbase.h>  
[module(name="Test")];  
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {  
   [case(24)]  
      float fM;  
   [case(25)]  
      double dMN;  
   [default]  
      int x;  
} TD_UNION_TYPE;  
  
[export, public] typedef struct _TDW_TYPE {  
   [switch_is(sU)] TD_UNION_TYPE w;  
      short sU;  
} TD_TYPE;  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface I {  
   HRESULT f(TD_TYPE*);  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct C : I {  
   HRESULT f(TD_TYPE*) { return 0; }  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4929.  
  
```  
// C4929b.cpp  
// compile with: /c /W1  
#import "C4929a.tlb" embedded_idl   // C4929  
```