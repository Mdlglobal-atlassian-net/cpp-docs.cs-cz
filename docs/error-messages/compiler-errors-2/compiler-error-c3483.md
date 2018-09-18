---
title: Chyba kompilátoru C3483 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: decc04f25689b24c560f59a71fd22a9708754352
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091683"
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