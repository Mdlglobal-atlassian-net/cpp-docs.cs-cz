---
title: Kompilátoru (úroveň 2) upozornění C4285 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4285
dev_langs:
- C++
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4366142c14ec77c1c344312e50e7295c71ca93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4285"></a>C4285 kompilátoru upozornění (úroveň 2)
Návratový typ pro -> identifier::operator je rekurzivní, pokud se aplikují pomocí notace zaváděcí  
  
 Zadaný **operátor -> ()** funkce nemůže vrátit je typu, pro která je definována, nebo odkaz na typ, pro který je definován.  
  
 Následující ukázka generuje C4285:  
  
```  
// C4285.cpp  
// compile with: /W2  
class C  
{  
public:  
    C operator->();   // C4285  
   // C& operator->();  C4285, also  
};  
  
int main()  
{  
}  
```