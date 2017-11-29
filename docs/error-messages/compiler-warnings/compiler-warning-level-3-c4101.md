---
title: "Kompilátoru (úroveň 3) upozornění C4101 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4101
dev_langs: C++
helpviewer_keywords: C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: edd99402978a41a115afa2d96f86abd63d72afa4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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