---
title: Kompilátoru (úroveň 4) upozornění C4709 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4709
dev_langs:
- C++
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aab1727ab667a4434805f969b32957e654814166
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295315"
---
# <a name="compiler-warning-level-4-c4709"></a>C4709 kompilátoru upozornění (úroveň 4)
Operátor čárky v rámci výraz index pole  
  
 Dojde-li k čárkou ve výrazu index pole, kompilátor použije hodnotu za poslední čárkou.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4709:  
  
```  
// C4709.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main()   
{  
    int arr[2][2];  
    arr[0][0] = 10;  
    arr[0][1] = 11;  
  
    // Prints 10, not 11  
    printf_s("\n%d",arr[0][1,0]);   // C4709  
}  
```