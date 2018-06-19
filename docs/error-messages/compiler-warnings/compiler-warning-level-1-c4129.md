---
title: Kompilátoru (úroveň 1) upozornění C4129 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc095a32e5cb0d5a0bf240282e11c3fa3382ffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276640"
---
# <a name="compiler-warning-level-1-c4129"></a>C4129 kompilátoru upozornění (úroveň 1)
'znak': nerozpoznaný znak – řídicí sekvence  
  
 `character` Následující zpětné lomítko (\\) v znak nebo řetězec konstanta není rozpoznán jako platná řídicí sekvence. Zpětné lomítko bude ignorován a ne k tisku. Je vytištěno znak následující zpětné lomítko.  
  
 Pokud chcete vytisknout jedno zpětné lomítko, zadejte dvojité zpětné lomítko (\\\\).  
  
 Standard C++ v části 2.13.2 popisuje řídicí sekvence.  
  
 Následující ukázka generuje C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```