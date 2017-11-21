---
title: "C2494 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2494
dev_langs: C++
helpviewer_keywords: C2494
ms.assetid: 5dfd07ab-351d-49c9-b54e-f0a104776ab8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 742bf081c8bb6f0309dc53dc30b66f38324c92ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2494"></a>C2494 chyby kompilátoru
'– klíčové slovo' nelze volat v rámci výraz filtru nebo blokovat __finally/finally  
  
 Nemůžete použít `keyword` v `__finally` nebo nakonec blokovat.  
  
 Následující ukázka generuje C2494:  
  
```  
// C2494.cpp  
#include <malloc.h>  
  
int main() {  
   __try {}  
   __except ( _alloca(100), 1 ) {}   // C2494  
   __try {}  
   __finally {  
      _alloca(100);   // C2494  
   }  
}  
```  
  
 C2494 může také nastat, pokud používáte **/CLR**.  
  
```  
// C2494b.cpp  
// compile with: /clr  
#include <malloc.h>  
  
int main() {  
   char * buf;  
   try {}  
   catch (char * buf2) {}  
   finally {  
      _alloca(100);   // C2494  
   }  
}  
```