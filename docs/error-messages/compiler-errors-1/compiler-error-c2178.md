---
title: C2178 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3727a66554b2e128061820df160c02a1370ebb74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171292"
---
# <a name="compiler-error-c2178"></a>C2178 chyby kompilátoru  
  
'*identifikátor*'nelze deklarovat s'*specifikátor*' – specifikátor  
  
A `mutable` specifikátor byla použita v deklaraci, ale specifikátor není v tomto kontextu povolen.  
  
`mutable` Specifikace lze použít pouze na názvy členy třídy data a nelze použít pro názvy deklarovaný `const` nebo `static`a nelze ji použít k odkazování členů.  
  
## <a name="example"></a>Příklad  
  
Následující příklad ukazuje, jak může dojít, C2178 a jeho řešení.  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  
