---
title: C2395 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 411a8d62de801591ff6a90a7bf74f3b2cfe67c7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2395"></a>C2395 chyby kompilátoru
' your_type::operator'op'': CLR nebo WinRT operátor není platný. Minimálně jeden parametr musí být z následujících typů: 'T', se %', se &', se ^', se ^ %', se ^ &', kde T = 'your_type'  
  
 Operátor v prostředí Windows Runtime nebo spravovaný typ neměl minimálně jeden parametr, jehož typ je stejný jako typ vrácené hodnoty operátor.  
  
 Následující ukázka generuje C2395 a ukazuje, jak to opravit:  
  
```  
// C2395.cpp  
// compile with: /clr /c  
value struct V {  
   static V operator *(int i, char c);   // C2395  
  
   // OK  
   static V operator *(V v, char c);  
   // or  
   static V operator *(int i, V& rv);  
};  
```