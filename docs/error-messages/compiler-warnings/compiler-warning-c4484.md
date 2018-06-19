---
title: C4484 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75531c207f0136f16109b4d69d689b883998aae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274752"
---
# <a name="compiler-warning-c4484"></a>C4484 upozornění kompilátoru
'override_function': odpovídá metody třídy base ref 'base_class_function', ale nebyla označena 'virtuální', 'nové' nebo 'přepsat'; se předpokládá, new' (a ne virtuální)  
  
 Při kompilaci s **/CLR**, kompilátor nebude přepsat implicitně funkce základní třídy, to znamená mít nový slot v tabulce vtable funkce. Pokud chcete vyřešit, explicitně určete, zda je funkce přepsání.  
  
 Další informace naleznete v tématu:  
  
-   [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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