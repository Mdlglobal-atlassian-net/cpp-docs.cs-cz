---
title: Chyba kompilátoru C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 7da9da2daedc79db619f82848dc864d1cb7bd1f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750088"
---
# <a name="compiler-error-c3531"></a>Chyba kompilátoru C3531

' symbol ': symbol, jehož typ obsahuje ' auto ', musí mít inicializátor

Zadaná proměnná neobsahuje výraz inicializátoru.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Zadejte výraz inicializátoru, jako je například jednoduché přiřazení, které používá syntaxi se znaménkem rovnost při deklaraci proměnné.

## <a name="example"></a>Příklad

Následující příklad vrací C3531, protože proměnné `x1`, `y1, y2, y3`a `z2` nejsou inicializovány.

```cpp
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

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
