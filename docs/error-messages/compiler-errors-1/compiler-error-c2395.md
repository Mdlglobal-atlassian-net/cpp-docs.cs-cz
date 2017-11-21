---
title: "C2395 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2395
dev_langs: C++
helpviewer_keywords: C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9190f4ef8a9db2daa29c6e2c3a59e0152c05d38a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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