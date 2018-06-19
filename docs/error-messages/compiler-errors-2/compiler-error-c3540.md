---
title: C3540 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256041"
---
# <a name="compiler-error-c3540"></a>C3540 chyby kompilátoru
'type': sizeof nelze použít na typ, který obsahuje 'auto'  
  
 [Sizeof](../../cpp/sizeof-operator.md) operátor nelze použít pro zadaný typ, protože obsahuje `auto` specifikátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3540.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof – operátor](../../cpp/sizeof-operator.md)