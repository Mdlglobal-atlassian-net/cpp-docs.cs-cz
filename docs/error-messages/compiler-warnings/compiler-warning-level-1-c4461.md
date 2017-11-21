---
title: "Kompilátoru (úroveň 1) upozornění C4461 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4461
dev_langs: C++
helpviewer_keywords: C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc417e7044eb3eac12365676c6c1be9abeddfed0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4461"></a>C4461 kompilátoru upozornění (úroveň 1)
'type': Tato třída obsahuje finalizační metodu 'finalizační metodu, ale žádné 'dtor' – destruktor  
  
 Přítomnost finalizační metodu v typu znamená prostředky odstranit. Pokud finalizační metody je explicitně volána z tohoto typu destruktor, modul common language runtime určuje, kdy se má spustit finalizační metodu, po objektu ocitne mimo rozsah.  
  
 Pokud definujete destruktor v typu a explicitně z destruktoru zavolat finalizační metodu, můžete spustit nepodmíněně vaše finalizační metodu.  
  
 Další informace najdete v tématu [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4461.  
  
```  
// C4461.cpp  
// compile with: /W1 /clr /c  
ref class A {  
protected:  
   !A() {}   // C4461  
};  
  
// OK  
ref struct B {  
   ~B() {  
      B::!B();  
   }  
  
   !B() {}  
};  
```