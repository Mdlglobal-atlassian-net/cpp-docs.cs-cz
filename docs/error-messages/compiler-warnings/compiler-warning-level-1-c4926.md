---
title: Kompilátoru (úroveň 1) upozornění C4926 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527c03d4f71048064c2120f7cfa9730de198fd46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290852"
---
# <a name="compiler-warning-level-1-c4926"></a>C4926 kompilátoru upozornění (úroveň 1)
"identifikátor": symbol je již definován: atributy ignorovat  
  
 Byl nalezen deklaraci předat dál, ale s atributy konstrukce se stejným názvem již existuje. Atributy dopředného deklaraci se ignorují.  
  
 Následující ukázka generuje C4926:  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```