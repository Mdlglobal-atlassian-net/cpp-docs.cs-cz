---
title: "Kompilátoru (úroveň 1) upozornění C4461 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3b3a64ac5d7bcfbc912c63abf57769fe6da2d40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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