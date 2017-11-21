---
title: "C3485 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3485
dev_langs: C++
helpviewer_keywords: C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd49b93beb54776bf17a9ee2bc5c9816f0964451
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)