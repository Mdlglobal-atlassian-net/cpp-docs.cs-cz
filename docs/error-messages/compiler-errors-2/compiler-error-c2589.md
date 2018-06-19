---
title: C2589 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230750"
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