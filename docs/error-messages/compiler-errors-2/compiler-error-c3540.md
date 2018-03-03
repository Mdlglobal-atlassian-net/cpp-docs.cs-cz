---
title: "C3540 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3befc331c4f43f4efd4e5039258e0faddae97db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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