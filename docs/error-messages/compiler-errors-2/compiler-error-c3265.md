---
title: C3265 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3265
dev_langs:
- C++
helpviewer_keywords:
- C3265
ms.assetid: 10ab3e17-4a9f-4120-bab5-21473869b70f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97ebe9d44074b9e6915f577cc012d9e148b2fbb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3265"></a>C3265 chyby kompilátoru
nelze deklarovat spravované 'spravované konstrukt' v nespravované 'nespravované konstrukce.  
  
Nesmí obsahovat spravovaného objektu v kontextu nespravované.  
  
Následující příklad se shoduje s C3265:  
  
```  
// C3265_2.cpp  
// compile with: /clr /LD  
#include <vcclr.h>  
  
ref class A { };  
  
class B  
// try the following line instead  
// ref class B   
{  
   A ^a;   // C3265  
   // or embed the managed handle using gcroot  
   // try the following line instead  
   // gcroot<A^> a;  
};  
```  
