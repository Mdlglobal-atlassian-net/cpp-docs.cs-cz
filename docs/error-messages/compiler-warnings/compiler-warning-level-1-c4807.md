---
title: "Kompilátoru (úroveň 1) upozornění C4807 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4807
dev_langs: C++
helpviewer_keywords: C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af604a1a045b9dbef7b3c27f9c7aabd0040aa318
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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