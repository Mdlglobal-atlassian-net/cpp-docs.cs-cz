---
title: "C2391 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2391
dev_langs: C++
helpviewer_keywords: C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 573cea44b0a39ff3cc0dff4469aa8c5f5a2459e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2391"></a>C2391 chyby kompilátoru
"identifikátor": během definice typu nelze použít, přítele.  
  
 `friend` Deklarace zahrnuje deklaraci dokončení třídy. A `friend` deklarace můžete zadat členské funkce nebo specifikátor propracována typu, ale není deklaraci dokončení třídy.  
  
 Následující ukázka generuje C2326:  
  
```  
// C2391.cpp  
// compile with: /c  
class D {   
   void func( int );   
};  
  
class A {  
   friend class B { int i; };   // C2391  
  
   // OK  
   friend class C;  
   friend void D::func(int);  
};  
```