---
title: C3851 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82104776b2d1153310d0552bd873238333e746f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3851"></a>C3851 chyby kompilátoru
"char": universal znak name nelze určit znak v základní znakové sady  
  
 V kódu kompilovány jako C++ nemůžete použít název universal znaku představující znak ve znakové sadě základní zdroj mimo řetězec nebo znak literálu. Další informace najdete v tématu [znakových sad](../../cpp/character-sets.md). V kódu kompilovány jako C nelze použijete název universal znak znaků v rozsahu 0x20-0x7f, včetně, s výjimkou 0x24 ('$'), 0x40 (' @'), nebo 0x60 ('' ').  
  
 Následující ukázky generovat C3851 a ukazují, jak to opravit:  
  
```cpp  
// C3851.cpp  
int main()  
{  
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set  
   int test2_A = 0;        // OK  
}  
```