---
title: C3485 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cd9de6f300fed673d588df60d7acca15b104b61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3485"></a>C3485 chyby kompilátoru
definice lambda nemůže mít žádné kvalifikátory odchylka nákladů  
  
 Nelze použít `const` nebo `volatile` kvalifikátor jako součást definice výrazu lambda.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `const` nebo `volatile` kvalifikátor definice výrazu lambda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3485, protože používá `const` kvalifikátor jako součást definice výrazu lambda:  
  
```  
// C3485.cpp  
  
int main()  
{  
   auto x = []() const mutable {}; // C3485  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)