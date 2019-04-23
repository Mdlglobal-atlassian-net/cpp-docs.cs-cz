---
title: Chyba kompilátoru C3531
ms.date: 11/04/2016
f1_keywords:
- C3531
helpviewer_keywords:
- C3531
ms.assetid: 2bdb9fdc-9ddf-403e-8b92-02763d434487
ms.openlocfilehash: 6961d99d1a0d7d0ea063aee5544a1009af2547c7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031258"
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

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)