---
title: "C2422 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2422
dev_langs:
- C++
helpviewer_keywords:
- C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 852a495406a8baf147fc53262f8fe856fce726b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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