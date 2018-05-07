---
title: Upozornění (úroveň 2) C4244 kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4244
dev_langs:
- C++
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de3b2392575f069c9ffc7b661cbd647f81f9557b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4244"></a>Kompilátoru upozornění (úroveň 2) C4244
'argument': 'type1' převod na 'type2', možné ztrátě dat.  
  
 A plovoucí typ bodu byl převeden na typ integer.  Případné ztrátě dat, mohlo dojít.  
  
 Pokud se zobrazí C4244, by měl buď změnit program používat typy kompatibilní, nebo přidat některé logiku kód, a ujistěte se, že rozsahu možných hodnot bude vždy kompatibilní s typy, které používáte.  
  
 C4244 můžete také provést na úrovni 3 a 4; v tématu [upozornění kompilátoru (úrovně 3 a 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4244:  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```