---
title: "C3488 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3488
dev_langs: C++
helpviewer_keywords: C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5006ca7cb3477730a4234a8e058acdae520a59c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3488"></a>C3488 chyby kompilátoru
'příkaz var' není povolená, pokud je výchozí režim zachycení odkazem  
  
 Pokud určíte, že je výchozí režim zachycení pro výraz lambda odkazem, nemůžete předat proměnné s odkazem na klauzuli zachycení tohoto výrazu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Proměnná explicitně nepředávejte pro klauzuli zachycení nebo  
  
-   Nezadávejte odkazem jako výchozí režim zachycení, nebo  
  
-   Zadejte-hodnota jako výchozí režim zachycení, nebo  
  
-   Předejte proměnnou hodnotou klauzuli zachycení. (Toto může změnit chování výrazu lambda.)  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3488, protože odkaz na proměnnou `n` se zobrazí v klauzuli zachycení výrazu lambda, jejíž výchozí režim je odkazem:  
  
```  
// C3488a.cpp  
  
int main()  
{  
   int n = 5;  
   [&, &n]() { return n; } (); // C3488  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na C3488 čtyři možná řešení:  
  
```  
// C3488b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass &n to the capture clause.  
   [&]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-reference as the default capture mode.  
   [&n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-value as the default capture mode.  
   [=, &n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by value to the capture clause.  
   [n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)