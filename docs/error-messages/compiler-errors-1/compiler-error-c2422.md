---
title: "C2422 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2422
dev_langs: C++
helpviewer_keywords: C2422
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65412576c3c1a5e6b8205652d826d0eca6d222e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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