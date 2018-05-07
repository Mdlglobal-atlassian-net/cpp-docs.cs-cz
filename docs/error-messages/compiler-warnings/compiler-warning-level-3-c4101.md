---
title: Kompilátoru (úroveň 3) upozornění C4101 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4101
dev_langs:
- C++
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 973b966e4b589cb35ffc92da9031779b14d448e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4101"></a>C4101 kompilátoru upozornění (úroveň 3)
"identifikátor": neregistrované místní proměnné  
  
 Místní proměnné se nikdy nepoužívá. Toto upozornění se budou provedeny v zřejmé situaci:  
  
```  
// C4101a.cpp  
// compile with: /W3  
int main() {  
int i;   // C4101  
}  
```  
  
 Ale toto upozornění se také stane, když volání **statické** funkce člena prostřednictvím instance třídy:  
  
```  
// C4101b.cpp  
// compile with:  /W3  
struct S {  
   static int func()  
   {  
      return 1;  
   }  
};  
  
int main() {  
   S si;   // C4101, si is never used  
   int y = si.func();  
   return y;  
}  
```  
  
 V takovém případě kompilátor používá informace o `si` pro přístup k **statické** funkce, ale instanci třídy není potřebných k volání **statické** funkce; proto upozornění. Chcete-li vyřešit toto upozornění, vám může:  
  
-   Přidejte konstruktor, ve kterém by kompilátor používat instanci `si` ve volání `func`.  
  
-   Odeberte **statické** – klíčové slovo z definice `func`.  
  
-   Volání **statické** funkce explicitně: `int y = S::func();`.