---
title: "Kompilátoru (úroveň 4) upozornění C4516 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4516
dev_langs: C++
helpviewer_keywords: C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 093dbd6a860b6bf0c65753afe104efa377c2db7a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4516"></a>C4516 kompilátoru upozornění (úroveň 4)
'class::symbol': deklarace přístupu jsou zastaralé; člen pomocí deklarace poskytovat lepší alternativou  
  
 ANSI C++ výbor deklaruje přístup deklarace (Změna přístup člena v odvozené třídě bez [pomocí](../../cpp/using-declaration.md) – klíčové slovo) jako zastaralé. Deklarace přístup nemusí být podporována budoucích verzích C++.  
  
 Následující ukázka generuje C4516:  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```