---
title: Kompilátoru (úroveň 1) upozornění C4333 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4333
dev_langs:
- C++
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67fb838ecbf34f1fb09242a93f6943d81fd0de1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282460"
---
# <a name="compiler-warning-level-1-c4333"></a>C4333 kompilátoru upozornění (úroveň 1)
'operátor': posunutí doprava o příliš velké množství, ztráty dat  
  
 Posunutí doprava operaci byla příliš velká dobu.  Všechny významných bitů posunuty a výsledek bude vždy nula.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4333.  
  
```  
// C4333.cpp  
// compile with: /c /W1  
unsigned shift8 (unsigned char c) {  
   return c >> 8;   // C4333  
  
   // try the following line instead  
   // return c >> 4;   // OK  
}  
```