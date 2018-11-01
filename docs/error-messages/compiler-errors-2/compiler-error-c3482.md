---
title: Chyba kompilátoru C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: ec0018fc1aafc7e3e0423608f4db9f78946e4597
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432636"
---
# <a name="compiler-error-c3482"></a>Chyba kompilátoru C3482

"this" jde použít jenom jako zachycení lambdy v rámci funkce nestatického člena

Nelze předat `this` na seznamu zachycení výrazu lambda, který je deklarován v statickou metodu nebo globálními funkcemi.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Převést na nestatické metody nadřazené funkce nebo

- Odeberte `this` ukazatele v seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3482:

```
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)