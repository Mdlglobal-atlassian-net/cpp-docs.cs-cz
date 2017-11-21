---
title: "Kompilátoru (úroveň 3) upozornění C4995 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4995
dev_langs: C++
helpviewer_keywords: C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65fcab42a09de35db8df82ed3d4b5c16a5d60177
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4995"></a>C4995 kompilátoru upozornění (úroveň 3)
'function': název byl označen jako zastaralý #pragma  
  
 Kompilátor došlo k funkci, která byla označena – Direktiva pragma [zastaralé](../../preprocessor/deprecated-c-cpp.md). Tato funkce již nemusí být v některé budoucí verzi podporována. Můžete vypnout toto upozornění se [upozornění](../../preprocessor/warning.md) – Direktiva pragma (třeba níže).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4995:  
  
```  
// C4995.cpp  
// compile with: /W3  
#include <stdio.h>  
  
// #pragma warning(disable : 4995)  
void func1(void)  
{  
    printf("\nIn func1");  
}  
  
int main()   
{  
    func1();  
    #pragma deprecated(func1)  
    func1();   // C4995  
}  
```