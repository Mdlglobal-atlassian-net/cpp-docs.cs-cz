---
title: Kompilátoru (úroveň 1) upozornění C4731 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31bdf972ef3791760469251dc4d0bf19627bded2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283878"
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