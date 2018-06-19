---
title: Kompilátoru (úroveň 1) upozornění C4805 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4805
dev_langs:
- C++
helpviewer_keywords:
- C4805
ms.assetid: 99c7b7e2-272e-4ab5-8580-17c42e62e2ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13477b20a046741e845c84fd1812dbc6c547ccbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281561"
---
# <a name="compiler-warning-level-1-c4805"></a>C4805 kompilátoru upozornění (úroveň 1)
'operace': unsafe směs typu "typ" a typu "typ" v operaci  
  
 Toto upozornění je generováno pro operace porovnání mezi [bool](../../cpp/bool-cpp.md) a [int](../../c-language/integer-types.md). Následující ukázka generuje C4805:  
  
```  
// C4805.cpp  
// compile with: /W1  
int main() {  
   int i = 1;  
   bool b = true;  
  
   if (i == b) {   // C4805, comparing bool and int variables  
   }  
}  
```