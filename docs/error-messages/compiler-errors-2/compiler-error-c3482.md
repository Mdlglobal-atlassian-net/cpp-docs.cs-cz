---
title: Chyba kompilátoru C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 1d775551d0f4955dc4eda9b0d418ea31e065714f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743130"
---
# <a name="compiler-error-c3482"></a>Chyba kompilátoru C3482

klíčové slovo this se dá použít jedině jako zachycení lambdy v rámci nestatické členské funkce.

Nelze předat `this` do seznamu zachycení výrazu lambda, který je deklarován ve statické metodě nebo globální funkci.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Převeďte uzavírací funkci na nestatickou metodu nebo

- Odeberte ukazatel `this` ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3482:

```cpp
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
