---
title: Chyba kompilátoru C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 0f6094daddf40b0899dc7f341f50a31daf7a999b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435448"
---
# <a name="compiler-error-c3531"></a>Chyba kompilátoru C3531

'symbol': symbol, jehož typ obsahuje nastavení auto' musí mít inicializátor

Zadaná proměnná nemá inicializační výraz.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zadejte inicializační výraz, jako je například jednoduché přiřazení, která používá syntaxe znaménka rovnosti, když deklarujete proměnnou.

## <a name="example"></a>Příklad

Následující příklad provede C3531, protože proměnné `x1`, `y1, y2, y3`, a `z2` nejsou inicializovány.

```
// C3531.cpp
// Compile with /Zc:auto
int main()
{
   auto x1;                  // C3531
   auto y1, y2, y3;          // C3531
   auto z1 = 1, z2, z3 = -1; // C3531
   return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)