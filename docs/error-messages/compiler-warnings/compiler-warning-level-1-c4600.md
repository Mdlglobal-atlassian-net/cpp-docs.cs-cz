---
title: "Kompilátoru (úroveň 1) upozornění C4600 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4600
dev_langs: C++
helpviewer_keywords: C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 204f9c1964173143db23d4e8d5c7a7418f6aa2d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4600"></a>C4600 kompilátoru upozornění (úroveň 1)
\#Direktiva pragma "makro název": očekáván platný neprázdný řetězec  
  
 Nelze zadat prázdný řetězec, při nabízené nebo pop název makra s buď [pop_macro –](../../preprocessor/pop-macro.md) nebo [push_macro –](../../preprocessor/push-macro.md).  
  
 Následující ukázka generuje C4600:  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```