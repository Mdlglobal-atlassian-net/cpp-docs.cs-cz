---
title: "Kompilátoru (úroveň 2) upozornění C4285 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4285
dev_langs: C++
helpviewer_keywords: C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0893334b46ed4b0790996482dd5625978705d3ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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