---
title: "Kompilátoru (úroveň 1) upozornění C4731 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4731
dev_langs: C++
helpviewer_keywords: C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d8c59a22166c3f4f44db3bea43e241a2199009d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4731"></a>C4731 kompilátoru upozornění (úroveň 1)
'ukazatel': registr ukazatele 'zaregistrovat, upravit kód vnořeného sestavení s rámečkem  
  
 Registr ukazatele rámce byla změněna. Musí uložení a obnovení registru v vaše vloženého sestavení bloku nebo rámce proměnná (místní nebo parametr, v závislosti na registraci změnil) nebo váš kód nemusí fungovat správně.  
  
 Následující ukázka generuje C4731:  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP je ukazatel na rámec (FPO je zakázaná) a je upravována. Když `p` později odkazuje, se vzhledem k odkazuje `EBP`. Ale `EBP` přepsán pomocí kódu, tak, aby tento program nebude fungovat správně a dojít i k chybě.