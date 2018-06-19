---
title: Kompilátoru (úroveň 1) upozornění C4461 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2884daeb7497f6664cecf864ec705891cac62f48
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278630"
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