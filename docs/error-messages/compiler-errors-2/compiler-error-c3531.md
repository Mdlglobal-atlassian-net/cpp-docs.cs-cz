---
title: "C3531 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3531
dev_langs:
- C++
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7c8158d798df3fb48c45194ff6a01a1cbf3ab4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3531"></a>C3531 chyby kompilátoru
'symbol': symbol, jehož typ obsahuje 'auto' musí mít inicializátoru  
  
 Zadanou proměnnou nemá inicializátoru výrazu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadejte výraz inicializátoru, jako je například jednoduché přiřazení, který používá syntaxi znaménkem rovnosti k deklarovat proměnnou.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3531, protože proměnné `x1`, `y1, y2, y3`, a `z2` nejsou inicializovány.  
  
```  
// C3531.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto x1;                  // C3531  
   auto y1, y2, y3;          // C3531  
   auto z1 = 1, z2, z3 = -1; // C3531  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)