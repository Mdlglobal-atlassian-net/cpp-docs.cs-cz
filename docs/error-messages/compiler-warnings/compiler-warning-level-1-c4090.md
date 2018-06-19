---
title: Kompilátoru (úroveň 1) upozornění C4090 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a28924b2cf176524a2ecd3156394dd7530cfb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276487"
---
# <a name="compiler-warning-level-1-c4090"></a>C4090 kompilátoru upozornění (úroveň 1)
'operace': kvalifikátory různých "modifikátor"  
  
 Proměnné použít v operaci je definována pomocí zadané modifikátor, která brání jeho upravuje bez detekce v kompilátoru. Výraz je kompilovat bez úprav.  
  
 Toto upozornění může dojít, když ukazatel **const** nebo `volatile` položka přiřazena ukazatel není deklarován jako odkazující na **const** nebo `volatile`.  
  
 Pro programy C se objeví toto upozornění. V programu C++, vydá chybu: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 Následující ukázka generuje C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```