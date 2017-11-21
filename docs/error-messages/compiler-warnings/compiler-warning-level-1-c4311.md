---
title: "Kompilátoru (úroveň 1) upozornění C4311 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4311
dev_langs: C++
helpviewer_keywords: C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 85a07ff4477d52a2c9b60978c9f4ba00c2127906
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4311"></a>C4311 kompilátoru upozornění (úroveň 1)
'variable': zkrácení ukazatele z 'type' na 'type'  
  
 Toto upozornění zjišťuje ukazatele 64-bit zkrácení problémy. Například pokud kompilace kódu pro architekturu 64-bit hodnota ukazatele (64bitová verze) bude zkrácen když je přiřazena `int` (32bitová verze). Další informace najdete v tématu [pravidla pro používání ukazatele](http://msdn.microsoft.com/library/windows/desktop/aa384242).  
  
 Další informace o běžných příčin upozornění C4311 najdete v tématu [běžné chyby kompilátoru](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 Následující příklad kódu generuje C4311 při kompilaci pro 64bitové cílové a pak ukazuje, jak to opravit:  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```