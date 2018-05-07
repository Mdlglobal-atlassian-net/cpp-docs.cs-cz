---
title: C3052 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3052
dev_langs:
- C++
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96db942b0ed50114378843b9f88fd77b2d24d771
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3052"></a>C3052 chyby kompilátoru
'příkaz var': proměnné se nezobrazí v klauzuli sdílení dat v klauzuli default(none)  
  
 Pokud [default(none)](../../parallel/openmp/reference/default-openmp.md) se používá, všechny proměnné používané v strukturovaných bloku musí být explicitně zadány jako buď [sdílené](../../parallel/openmp/reference/shared-openmp.md) nebo [privátní](../../parallel/openmp/reference/private-openmp.md).  
  
 Následující ukázka generuje C3052:  
  
```  
// C3052.cpp  
// compile with: /openmp /c  
int main() {  
   int n1 = 1;  
  
   #pragma omp parallel default(none) // shared(n1) private(n1)  
   {  
      n1 = 0;   // C3052 use either a shared or private clause  
   }  
}  
```