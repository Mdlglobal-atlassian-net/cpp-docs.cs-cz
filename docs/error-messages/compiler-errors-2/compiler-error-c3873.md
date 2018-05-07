---
title: C3873 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bec37b8fb00aedd83d91f1d001d77c42679ec038
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3873"></a>C3873 chyby kompilátoru
"char": Tento znak není povolen jako první znak identifikátoru  
  
 Kompilátor C++ odpovídá C ++ 11 standard na povolených znaků v identifikátor. V identifikátoru jsou povoleny pouze určitý rozsah znaků a univerzální názvy znaků. Další omezení se použijí na počáteční znak identifikátoru. Další informace a seznam povolených a rozsahy název universal znaků najdete v tématu [identifikátory](../../cpp/identifiers-cpp.md).  
  
 Rozsah znaků povolených v identifikátoru je méně omezující při kompilování C + +/ CLI kódu. Postupujte podle identifikátory v kódu zkompilovat pomocí/CLR [standardní standardy ECMA-335: společné jazykové infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Následující ukázka generuje C3873:  
  
```  
// C3873.cpp  
int main() {  
   int \u036F_abc;   // C3873, not in allowed range for initial character  
   int abc_\u036F;   // OK, in allowed range for non-initial character  
}  
```