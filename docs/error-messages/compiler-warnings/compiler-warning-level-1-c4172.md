---
title: Kompilátoru (úroveň 1) upozornění C4172 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746442638820d0c81144611a678996dc4c8483b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4172"></a>C4172 kompilátoru upozornění (úroveň 1)
Vrátí adresu místní proměnné nebo dočasné  
  
 Funkce vrátí adresu místní proměnné nebo dočasný objekt. Místní proměnné a dočasné objekty jsou zničený, když se vrátí funkci, tak vrátila adresa není platná.  
  
 Změnit návrh funkci tak, aby se nevrátí na adresu místního objektu.  
  
 Následující ukázka generuje C4172:  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```