---
title: "Kompilátoru (úroveň 3) upozornění C4265 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4265
dev_langs: C++
helpviewer_keywords: C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 59dd816641748061d3d5316a2a61b342bec876fe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4265"></a>C4265 kompilátoru upozornění (úroveň 3)
'class': třída má virtuální funkce, ale není virtuální – destruktor  
  
 Třída má virtuální funkce ale nevirtuální destruktor, objekty typu nemusí zničen správně, pokud třída zničen prostřednictvím ukazatele základní třídy.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4265:  
  
```  
// C4265.cpp  
// compile with: /W3 /c  
#pragma warning(default : 4265)  
class B  
{  
public:  
   virtual void vmf();  
  
   ~B();  
   // try the following line instead  
   // virtual ~B();  
};   // C4265  
  
int main()  
{  
   B b;  
}  
```