---
title: "C4484 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa5f209dd3a77bcc4ec3c21d589fb8ba1ed3faf1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4484"></a>C4484 upozornění kompilátoru
'override_function': odpovídá metody třídy base ref 'base_class_function', ale nebyla označena 'virtuální', 'nové' nebo 'přepsat'; se předpokládá, new' (a ne virtuální)  
  
 Při kompilaci s **/CLR**, kompilátor nebude přepsat implicitně funkce základní třídy, to znamená mít nový slot v tabulce vtable funkce. Pokud chcete vyřešit, explicitně určete, zda je funkce přepsání.  
  
 Další informace naleznete v tématu:  
  
-   [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [New (nový slot v tabulce vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 C4484 je vždy vydané jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro potlačení C4484.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4484.  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```