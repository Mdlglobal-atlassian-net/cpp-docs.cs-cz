---
title: Kompilátoru (úroveň 3) upozornění C4316 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 609f3bbe9f338c5d53491190512ce2b9c290cdb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4316"></a>C4316 kompilátoru upozornění (úroveň 3)
Pro tento typ nemusí být zarovnána objekt přidělené v haldě.  
  
 Objekt přepsání zarovnaný přidělené pomocí `operator new` nemusí mít zadané zarovnání. Přepsání [new – operátor](../../c-runtime-library/operator-new-crt.md) a [delete – operátor](../../c-runtime-library/operator-delete-crt.md) pro přepsání zarovnán typy tak, aby používají rutiny zarovnaný přidělení – například [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) a [_aligned_free –](../../c-runtime-library/reference/aligned-free.md). Následující ukázka generuje C4316:  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```