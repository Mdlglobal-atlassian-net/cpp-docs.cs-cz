---
title: Chyba kompilátoru C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 0eacb6ce6426674d23fc78596ead3730f46ae370
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743039"
---
# <a name="compiler-error-c3485"></a>Chyba kompilátoru C3485

definice lambda nemůže mít žádné kvalifikátory cv.

Kvalifikátor `const` ani `volatile` nelze použít jako součást definice výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte kvalifikátor `const` nebo `volatile` z definice výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3485, protože používá kvalifikátor `const` jako součást definice výrazu lambda:

```cpp
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
