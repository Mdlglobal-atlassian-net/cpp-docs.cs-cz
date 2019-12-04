---
title: Chyba kompilátoru C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: 37129c198096be91a8104aedcb508732d79e3630
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738307"
---
# <a name="compiler-error-c3492"></a>Chyba kompilátoru C3492

var: nejde zachytit člen anonymního sjednocení.

Nejde zachytit člen nepojmenované sjednocení.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Dejte sjednocení název a předejte kompletní strukturu sjednocení do seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3492, protože zachycuje člena anonymního sjednocení:

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

## <a name="example"></a>Příklad

Následující příklad vyřeší C3492 přidělením názvu Union a předáním úplné struktury sjednocení do seznamu zachycení výrazu lambda:

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
