---
title: "Kompilátoru (úroveň 4) upozornění C4626 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4626
dev_langs: C++
helpviewer_keywords: C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a280faadea23ced85c5b8256fd6b00c8d84370f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4626"></a>C4626 kompilátoru upozornění (úroveň 4)
odvozené třídy': operátor přiřazení byl implicitně definován jako odstranit, protože operátor přiřazení základní třída je nedostupný, nebo odstraněné  
  
 Operátor přiřazení byl odstraněný nebo není k dispozici v základní třídě a nebyl proto vygenerované odvozené třídy. Chyba kompilátoru způsobí, že pokusy o přiřazovat objekty tohoto typu.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4626 a ukazuje, jak to opravit:  
  
```  
// C4626  
// compile with: /W4  
#pragma warning(default : 4626)  
class B  
{  
// public:  
   B& operator = (const B&)  
   {  
      return *this;  
   }  
};  
  
class D : public B  
{  
  
}; // C4626 - to fix, make B's copy constructor public  
  
int main()  
{  
   D m;  
   D n;  
   // m = n;   // this line will cause an error  
}  
```