---
title: Chyba kompilátoru C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: acbe89b5183d0991fb8d4a571a9595d6f6bafc6c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026120"
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

## <a name="see-also"></a>Viz také:

[Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)