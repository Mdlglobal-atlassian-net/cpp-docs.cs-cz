---
title: Chyba kompilátoru C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 6ff269d719dd354932ef79946ae99a9b60490199
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173220"
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

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)