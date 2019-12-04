---
title: Chyba kompilátoru C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 940eae39222548ec74bda8ccb38e669748ffa74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738398"
---
# <a name="compiler-error-c3490"></a>Chyba kompilátoru C3490

vlastnost var nelze změnit, protože je k ní přistupovaná prostřednictvím objektu const.

Výraz lambda, který je deklarován v metodě `const`, nemůže upravovat data, která nejsou proměnlivá.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte modifikátor `const` z deklarace metody.

## <a name="example"></a>Příklad

Následující příklad generuje C3490, protože upravuje členskou proměnnou `_i` v metodě `const`:

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Příklad

Následující příklad vyřeší C3490 odebráním modifikátoru `const` z deklarace metody:

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
