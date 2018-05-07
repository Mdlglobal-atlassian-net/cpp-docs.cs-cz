---
title: C2422 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89a808e4b324b11c88be38ae7d8815bee4e232cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2422"></a>C2422 chyby kompilátoru
Neplatný segment potlačení v "operand.  
  
 Kód vnořeného sestavení nesprávně použit operátor přepsání segmentu (dvojtečka) na operand.  Možné příčiny:  
  
-   Registrace předcházející operátor není registr segmentu.  
  
-   Registrace předcházející operátor není pouze registr segmentu v operand.  
  
-   Operátor přepsání segmentu se zobrazí v rámci indirection – operátor (závorky).  
  
-   Výraz, který následuje operátor přepsání segment není přímým operandem nebo operand paměti.  
  
 Následující ukázka generuje C2422:  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```