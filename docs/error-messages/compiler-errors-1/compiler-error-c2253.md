---
title: "C2253 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2253
dev_langs: C++
helpviewer_keywords: C2253
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d804f3c9d0382d5e43f7c075d545f12879071330
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2253"></a>C2253 chyby kompilátoru
'function': pure specifikátor nebo abstraktní override – specifikátor povoleny pouze na virtuální funkce  
  
 Nevirtuální funkce je zadán jako čistý `virtual`.  
  
 Následující ukázka generuje C2253:  
  
```  
// C2253.cpp  
// compile with: /c  
class A {  
public:  
   void func1() = 0;   // C2253 not virtual  
   virtual void func2() = 0;   // OK  
};  
```  
  
 Následující ukázka generuje C2253:  
  
```  
// C2253_2.cpp  
// compile with: /clr /c  
ref struct A {  
   property int Prop_3 {  
      int get() abstract;   // C2253  
      // try the following line instead  
      // virtual int get() abstract;  
  
      void set(int i) abstract;   // C2253  
      // try the following line instead  
      // virtual void set(int i) abstract;  
   }  
};  
```