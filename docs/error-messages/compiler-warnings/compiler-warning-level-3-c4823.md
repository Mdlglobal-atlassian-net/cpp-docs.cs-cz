---
title: "Kompilátoru (úroveň 3) upozornění C4823 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4823
dev_langs: C++
helpviewer_keywords: C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18e041bd9a013779a37dc2460b8e1913b69d734b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4823"></a>C4823 kompilátoru upozornění (úroveň 3)
'function': používá přídavných ukazatelů ale unwind sémantiku nejsou povoleny. Zvažte použití/EHa  
  
Odepnout objektu na spravovaná halda ukazuje Připnutí ukazatel deklarován v oboru bloku, kompilátor simuluje chování destruktory místní třídy "předstírají, že" Připnutí ukazatelů má destruktor nichž ukazatele. Chcete-li povolit volání destruktoru po vyvolání výjimky, je nutné povolit objekt unwinding, což lze provést pomocí [/EHsc](../../build/reference/eh-exception-handling-model.md).  
  
Můžete také ručně Odepnout objekt a upozornění ignorovat.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C4823.  
  
```  
// C4823.cpp  
// compile with: /clr /W3 /EHa-  
using namespace System;  
  
ref struct G {  
   int m;  
};  
  
void f(G ^ pG) {  
   try {  
      pin_ptr<int> p = &pG->m;  
      // manually unpin, ignore warning  
      // p = nullptr;  
      throw gcnew Exception;  
   }  
   catch(Exception ^) {}  
}   // C4823 warning  
  
int main() {  
   f( gcnew G );  
}  
```  
