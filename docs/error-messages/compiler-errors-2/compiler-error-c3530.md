---
title: Chyba kompilátoru C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 90f6000c7d4c4bfa0d610bd5942df0b958e47c60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643623"
---
# <a name="compiler-error-c3530"></a>Chyba kompilátoru C3530

'auto' nelze kombinovat s jakékoli jiným specifikátorem typu.

Použití specifikátoru typu s `auto` – klíčové slovo.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Nepoužívejte specifikátor typu v deklaraci proměnné, která používá `auto` – klíčové slovo.

## <a name="example"></a>Příklad

Následující příklad provede C3530, protože proměnná `x` je deklarován s oběma `auto` – klíčové slovo a typ `int`, a protože příklad je zkompilován s **/Zc: Auto**.

```
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)