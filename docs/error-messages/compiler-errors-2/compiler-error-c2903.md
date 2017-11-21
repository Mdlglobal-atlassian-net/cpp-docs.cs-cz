---
title: "C2903 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2903
dev_langs: C++
helpviewer_keywords: C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2241d4421c2fcee89b06bf176cfab9bb788693d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2903"></a>C2903 chyby kompilátoru
"identifikátor": symbol je šablona třídy ani šablonu – funkce  
  
 Kód pokusí explicitní vytvoření instance služby něco, není šablona.  
  
 Následující ukázka generuje C2903:  
  
```  
// C2903.cpp  
// compile with: /c  
namespace N {  
   template<class T> class X {};  
   class Y {};  
}  
void g() {  
   N::template Y y;   // C2903  
   N::X<N::Y> y;   // OK  
}  
```  
  
 C2903 může dojít také při použití obecných typů:  
  
```  
// C2903b.cpp  
// compile with: /clr /c  
namespace N {  
   class Y {};  
   generic<class T> ref class Z {};  
}  
  
void f() {  
   N::generic Y y;   // C2903  
   N:: generic Z<int>^ z;   // OK  
}  
```