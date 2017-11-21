---
title: "Kompilátoru (úroveň 1) upozornění C4997 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4997
dev_langs: C++
helpviewer_keywords: C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb9c3c0d2b48db5676c8510c75ef9e6bee42a160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4997"></a>C4997 kompilátoru upozornění (úroveň 1)
'class': Třída typu coclass neimplementuje rozhraní modelu COM nebo pseudorozhraní  
  
 Třída označené jako [třída typu coclass](../../windows/coclass.md) atribut neimplementovala rozhraní.  
  
 Následující ukázka generuje C4997:  
  
```  
// C4997.cpp  
// compile with: /WX  
// to resolve this C4997, uncomment all code  
#include <objbase.h>  
  
[ object ]  
__interface I {  
   HRESULT func();  
};  
  
[ coclass ]  
struct C /*: I*/ {  
   /*  
   HRESULT func() {  
      return S_OK;  
   }  
   */  
};   // C4997  
```