---
title: C3182 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3182
dev_langs:
- C++
helpviewer_keywords:
- C3182
ms.assetid: f3681266-308e-4990-a979-8eef8920e186
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503ad6d17b197392967681bfdf4e921aa21dc3e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3182"></a>C3182 chyby kompilátoru
'class': Deklarace členů pomocí deklarace nebo přístup není povolen v rámci spravované nebo WinRTtype  
  
 A [pomocí](../../cpp/using-declaration.md) deklarace je neplatný v rámci všech formulářů spravované třídy.  
  
 Následující ukázka generuje C3182 a ukazuje, jak ji odstranit.  
  
```  
// C3182a.cpp  
// compile with: /clr /c  
ref struct B {  
   void mf(int) {  
   }  
};  
  
ref struct D : B {  
   using B::mf;   // C3182, delete to resolve  
   void mf(char) {  
   }  
};  
```  
