---
title: C2675 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2675
dev_langs:
- C++
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb949f5d6ab5881b911bab89150ae13f47443fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235666"
---
# <a name="compiler-error-c2675"></a>C2675 chyby kompilátoru
Unární 'operátor': 'type' nedefinuje tento operátor nebo převod na typ přijatelné předdefinované operátor  
  
 C2675 může také nastat, pokud používáte unární operátor a typ nedefinuje operátor nebo převod na typ přijatelné předdefinované operátor. Chcete-li operátor použít, je třeba jej přetížit pro daný typ nebo definovat převod na typ, pro který je operátor definován.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2675.  
  
```  
// C2675.cpp  
struct C {   
   C(){}  
} c;  
  
struct D {   
   D(){}  
   void operator-(){}  
} d;  
  
int main() {  
   -c;   // C2675  
   -d;   // OK  
}  
```