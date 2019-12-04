---
title: Chyba kompilátoru C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 0d6c1467575e7fae7d5e4862f36e733a68210f8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743091"
---
# <a name="compiler-error-c3483"></a>Chyba kompilátoru C3483

klíčové slovo var už je součástí seznamu zachycení lambdy.

Stejnou proměnnou jste předali do seznamu zachycení výrazu lambda více než jednou.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odebere všechny další instance proměnné ze seznamu zachycení.

## <a name="example"></a>Příklad

Následující příklad vygeneruje C3483, protože proměnná `n` se v seznamu zachycení výrazu lambda vyskytuje více než jednou.

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
