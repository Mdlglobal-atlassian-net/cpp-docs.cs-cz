---
title: "Kompilátoru (úroveň 4) upozornění C4673 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4673
dev_langs: C++
helpviewer_keywords: C4673
ms.assetid: 95626ec6-f05b-43c7-8b9a-a60a6f98dd30
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8242a083fbf7a9f94c419c1cf142c7c1ada65009
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4673"></a>C4673 kompilátoru upozornění (úroveň 4)
vyvolání "identifikátor" následující typy nebude se zvažovat v lokalitě catch  
  
 Objekt throw nelze zpracovat v **catch** bloku. Každý typ, který nelze zpracovat, je uveden ve výstupu chyba okamžitě následující řádek obsahující toto upozornění. Každý typ neošetřené má svou vlastní upozornění. Přečtěte si upozornění pro každý typ konkrétní informace.  
  
 Následující ukázka generuje C4673:  
  
```  
// C4673.cpp  
// compile with: /EHsc /W4  
class Base {  
private:  
   char * m_chr;  
public:  
   Base() {  
      m_chr = 0;  
   }  
  
   ~Base() {  
      if(m_chr)  
         delete m_chr;  
   }  
};  
  
class Derv : private Base {  
public:  
   Derv() {}  
   ~Derv() {}  
};  
  
int main() {  
   try {  
      Derv D1;  
      // delete previous line, uncomment the next line to resolve  
      // Base D1;  
      throw D1;   // C4673  
   }  
  
   catch(...) {}  
}  
```