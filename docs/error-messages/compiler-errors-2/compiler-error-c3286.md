---
title: C3286 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3286
dev_langs:
- C++
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc47c103e93fe1e4f20f5007c6688b5b6648bf32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3286"></a>C3286 chyby kompilátoru  
  
> '*specifikátor*': Proměnná iterace nemůže mít žádné specifikátory třídy úložiště  
  
Třídy úložiště nelze zadat pro proměnnou iterací. Další informace najdete v tématu [třídy úložiště (C++)](../../cpp/storage-classes-cpp.md) a [, v](../../dotnet/for-each-in.md).  
  
## <a name="example"></a>Příklad  
  
Následující ukázka generuje C3286 a také zobrazuje správné použití.  
  
```cpp  
// C3286.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p = { 1, 2, 3 };  
   for each (static int i in p) {}   // C3286   
   for each (int j in p) {}   // OK  
}  
```