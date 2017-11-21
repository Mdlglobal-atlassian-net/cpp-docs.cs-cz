---
title: "C3285 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3285
dev_langs: C++
helpviewer_keywords: C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a517ec1b163f3092b8dd161bee6cb348ab0129c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3285"></a>C3285 chyby kompilátoru
pro každý příkaz nemůže pracovat s proměnnými typu "typ"  
  
 `for each` Příkaz opakuje skupinu embedded příkazy pro každý prvek v pole nebo objekt kolekce.  
  
 V tématu [, v](../../dotnet/for-each-in.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3285.  
  
```  
// C3285.cpp  
// compile with: /clr  
int main() {  
   for each (int i in 0) {}   // C3285   
  
   array<int> ^p = { 1, 2, 3 };  
   for each (int j in p) {}   // OK  
}  
```