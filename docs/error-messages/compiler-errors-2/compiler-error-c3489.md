---
title: "C3489 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4a0115bbb6d00a4e83d0ae3343b1af1b8024002
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3489"></a>C3489 chyby kompilátoru
'příkaz var' se vyžaduje, když je výchozí režim zachycení-hodnota  
  
 Pokud určíte, že je výchozí režim zachycení pro výraz lambda-hodnota, nemůžete předat proměnné hodnotou klauzuli zachycení tohoto výrazu.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Proměnná explicitně nepředávejte pro klauzuli zachycení nebo  
  
-   Nezadávejte-hodnota jako výchozí režim zachycení, nebo  
  
-   Zadejte odkazem jako výchozí režim zachycení, nebo  
  
-   Předejte proměnnou s odkazem na klauzuli zachycení. (Toto může změnit chování výrazu lambda.)  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3489 proměnná `n` se zobrazí podle hodnoty v klauzuli zachycení výraz lambda, jejíž výchozí režim je ve hodnota:  
  
```  
// C3489a.cpp  
  
int main()  
{  
   int n = 5;  
   [=, n]() { return n; } (); // C3489  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na C3489 čtyři možná řešení:  
  
```  
// C3489b.cpp  
  
int main()  
{  
   int n = 5;  
  
   // Possible resolution 1:  
   // Do not explicitly pass n to the capture clause.  
   [=]() { return n; } ();  
  
   // Possible resolution 2:  
   // Do not specify by-value as the default capture mode.  
   [n]() { return n; } ();  
  
   // Possible resolution 3:  
   // Specify by-reference as the default capture mode.  
   [&, n]() { return n; } ();  
  
   // Possible resolution 4:  
   // Pass n by reference to the capture clause.  
   [&n]() { return n; } ();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)