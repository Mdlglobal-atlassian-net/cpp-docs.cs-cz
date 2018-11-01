---
title: Chyba kompilátoru C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: c958eee234d25b008eb8cb03f40b45b8aaba81a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573456"
---
# <a name="compiler-error-c3483"></a>Chyba kompilátoru C3483

'příkaz var' je již součástí seznamu zachycení lambdy

Jste předali stejné proměnné do seznamu zachycení výrazu lambda více než jednou.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte všechny další instance proměnné ze seznamu zachycení.

## <a name="example"></a>Příklad

Následující příklad generuje C3483, protože proměnná `n` se zobrazí v seznamu zachycení výrazu lambda více než jednou:

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)