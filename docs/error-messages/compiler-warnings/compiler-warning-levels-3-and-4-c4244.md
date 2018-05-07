---
title: Upozornění (úrovně 3 a 4) C4244 kompilátoru | Microsoft Docs
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
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36908fa5f46cee0b86941ec630c3716c918e556f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Upozornění kompilátoru (úrovně 3 a 4) C4244
převod 'Převod' z 'type1' na 'type2', možné ztrátě dat.  
  
 Typ celé číslo je převedeno na menší hodnota typu integer. Toto je upozornění úrovně 4, pokud *type1* je `int` a *type2* je menší než `int`. Jinak je úroveň 3 (přiřazenou hodnotu typu [__int64](../../cpp/int8-int16-int32-int64.md) proměnné typu `unsigned int`). Případné ztrátě dat, mohlo dojít.  
  
 Pokud se zobrazí C4244, by měl buď změnit program používat typy kompatibilní, nebo přidat některé logiku kód, a ujistěte se, že rozsahu možných hodnot bude vždy kompatibilní s typy, které používáte.  
  
 C4244 můžete také provést na úrovni 2; v tématu [upozornění kompilátoru (úroveň 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) Další informace.  
  
 Převod může mít problém z důvodu implicitní převody.  
  
 Následující ukázka generuje C4244:  
  
```  
// C4244_level4.cpp  
// compile with: /W4  
int aa;  
unsigned short bb;  
int main() {  
   int b = 0, c = 0;  
   short a = b + c;   // C4244  
  
   bb += c;   // C4244  
   bb = bb + c;   // C4244  
   bb += (unsigned short)aa;   // C4244  
   bb = bb + (unsigned short)aa;   // OK  
}  
```  
  
 Další informace najdete v tématu [obvyklé aritmetické převody](../../c-language/usual-arithmetic-conversions.md).  
  
```  
// C4244_level3.cpp  
// compile with: /W3  
int main() {  
   __int64 i = 8;  
   unsigned int ii = i;   // C4244  
}  
```  
  
 Upozornění C4244 může dojít, když vytváření kódu pro 64bitové verze cíle, který negeneruje upozornění, při vytváření pro 32-bit cíle. Rozdíl mezi ukazatele je například 32-bit množství na platformách 32-bit, ale množství 64-bit na 64bitových platformách.  
  
 Následující ukázka generuje C4244 při kompilaci pro 64bitové cíle:  
  
```  
// C4244_level3_b.cpp  
// compile with: /W3   
int main() {  
   char* p1 = 0;  
   char* p2 = 0;  
   int x = p2 - p1;   // C4244  
}  
```