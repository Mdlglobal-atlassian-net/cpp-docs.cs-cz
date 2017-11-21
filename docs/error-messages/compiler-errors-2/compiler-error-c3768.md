---
title: "C3768 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3768
dev_langs: C++
helpviewer_keywords: C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d334473e326f28a628ebda9dede7a83340a1cb34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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