---
title: C3768 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3768
dev_langs:
- C++
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3634ecf3eb1417095cce144706838113b5ad2a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3768"></a>C3768 chyby kompilátoru
nelze převést na adresu virtuální vararg – funkce v čistě spravovaného kódu  
  
 **/CLR: pure** – možnost kompilátoru je zastaralá ve Visual Studiu 2015.  
  
 Při kompilaci s `/clr:pure`, nelze převést na adresu virtuální `vararg` funkce.  
  
## <a name="example"></a>Příklad  

 Následující ukázka generuje C3768:  
  
```  
// C3768.cpp  
// compile with: /clr:pure  
struct A  
{  
   virtual void f(...);  
};  
  
int main()  
{  
   &(A::f);   // C3768  
}  
```