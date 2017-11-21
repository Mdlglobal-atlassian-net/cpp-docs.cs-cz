---
title: "C2589 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2589
dev_langs: C++
helpviewer_keywords: C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5301caf0b52e61000a804e1d73b76343a8b7b2eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2589"></a>C2589 chyby kompilátoru
'identifikátor": neplatný token na pravé straně '::'  
  
 Pokud třída, struktura nebo union název se zobrazí vlevo od operátor řešení rozsahu (dvojité dvojtečky), je token na pravé straně musí být třída, struktura nebo členů sjednocení. Všechny globální identifikátor, jinak může vyskytovat na pravé straně.  
  
 Operátor řešení rozsahu nemohou být přetíženy.  
  
 Následující ukázka generuje C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```