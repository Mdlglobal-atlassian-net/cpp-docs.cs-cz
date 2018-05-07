---
title: C2748 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2748
dev_langs:
- C++
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 336a2eb10f0a39f81547361e982aa744be88149e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2748"></a>C2748 chyby kompilátoru
spravované nebo vytvoření WinRT pole musí mít velikost pole nebo pole inicializátoru  
  
 Spravovat A nebo pole WinRT špatně byl vytvořen. Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).  
  
 Následující ukázka generuje C2748 a ukazuje, jak to opravit:  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```