---
title: Kompilátoru (úroveň 1) upozornění C4600 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4600
dev_langs:
- C++
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7866268cffce31467e5306a969e981f310e91ace
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287511"
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