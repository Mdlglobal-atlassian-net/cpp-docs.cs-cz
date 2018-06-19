---
title: Kompilátoru (úroveň 1) upozornění C4807 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22710ee2b46a270e46aed7c043d4d988fcfaed62
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282360"
---
# <a name="compiler-warning-level-1-c4807"></a>C4807 kompilátoru upozornění (úroveň 1)
'operace': unsafe směs typu "typ" a podepsaný bitfield typu "typ"  
  
 Toto upozornění se vygeneruje, když jeden bit podepsané bitové pole k porovnání `bool` proměnné. Vzhledem k tomu, že jeden bit, podepsané bitové pole může obsahovat pouze hodnoty -1 nebo 0, je nebezpečné porovnat s `bool`. Žádná upozornění o kombinování `bool` a jeden bit, nepodepsané bitová pole vzhledem k tomu, že jsou identické `bool` a mohou obsahovat pouze 0 nebo 1.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4807:  
  
```  
// C4807.cpp  
// compile with: /W1  
typedef struct bitfield {  
   signed mybit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bool b = true;  
  
   // try..  
   // int b = true;  
  
   bf.mybit = -1;  
   if (b == bf.mybit) {   // C4807  
      b = false;  
   }  
}  
```