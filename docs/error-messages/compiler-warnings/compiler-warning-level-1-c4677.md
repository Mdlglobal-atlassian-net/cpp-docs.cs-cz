---
title: "Kompilátoru (úroveň 1) upozornění C4677 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4677
dev_langs: C++
helpviewer_keywords: C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a597fa2373de1a2650a86c0b8d4f51bad35d9818
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4677"></a>C4677 kompilátoru upozornění (úroveň 1)
'function': podpis privátního člena obsahuje privátní typ sestavení 'private_type.  
  
 Typ, který má veřejnou dostupnost mimo sestavení používá typ, který má privátní přístup mimo sestavení. Komponenty, která odkazuje na typ veřejných sestavení nebudou moci používat člena typu nebo členy, které odkazují na typ privátní sestavení.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4677.  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```