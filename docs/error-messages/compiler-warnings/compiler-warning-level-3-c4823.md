---
title: Kompilátoru (úroveň 3) upozornění C4823 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4823
dev_langs:
- C++
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c29499a82601dcf653ff2f003441935f1d6841a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293228"
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
