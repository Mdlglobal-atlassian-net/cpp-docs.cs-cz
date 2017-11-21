---
title: "Kompilátoru (úroveň 1) upozornění C4946 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4946
dev_langs: C++
helpviewer_keywords: C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 141067a495b3c5973f368d2319979cfc4c2df686
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4946"></a>C4946 kompilátoru upozornění (úroveň 1)
reinterpret_cast použito mezi souvisejícími třídami: 'class1' a 'class2'  
  
 Nepoužívejte [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) přetypovat mezi souvisejících typů. Použít [static_cast](../../cpp/static-cast-operator.md) místo nebo polymorfní typy pomocí [dynamic_cast](../../cpp/dynamic-cast-operator.md).  
  
 Ve výchozím nastavení je toto upozornění je vypnuté. Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Následující příklad kódu generuje C4946:  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```