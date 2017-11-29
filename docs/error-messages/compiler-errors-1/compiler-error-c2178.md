---
title: "C2178 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2178
dev_langs: C++
helpviewer_keywords: C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: facb255b0c53a3de0e1d5c9f90de5835b25e3c32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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