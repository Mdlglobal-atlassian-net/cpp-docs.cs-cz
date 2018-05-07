---
title: C2728 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e954ba38efc2e1ef7bc4b203c8b54876f7aae0ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2728"></a>C2728 chyby kompilátoru
'type': nativní pole nemůže obsahovat tento typ  
  
 Syntaxe vytváření pole byla použita k vytvoření pole spravované nebo WinRT objekty. Nelze vytvořit pole spravované nebo WinRT objekty pomocí syntaxe nativní pole.  
  
 Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).  
  
 Následující ukázka generuje C2728 a ukazuje, jak to opravit:  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
