---
title: "C2990 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2990
dev_langs: C++
helpviewer_keywords: C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9a2433bec7992c73fb7e9b7f358e89b7e75da384
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2990"></a>C2990 chyby kompilátoru
'class':-– Třída typu jako již byl deklarován jako typ – třída  
  
 Bez generic nebo šablony třídy znovu definuje třídu obecného nebo šablony. Zkontrolujte soubory hlaviček konflikty.  
  
 Následující ukázka generuje C2990:  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 C2990 může dojít také při použití obecných typů:  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 C2990 může také nastat z důvodu narušující změny v kompilátoru Visual C++ pro Visual C++ 2005; Kompilátor teď vyžaduje, aby více deklarací pro stejný typ identické s ohledem na specifikace šablony.  
  
 Následující ukázka generuje C2990:  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```