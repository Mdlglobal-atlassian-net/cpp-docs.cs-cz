---
title: Chyba kompilátoru C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761566"
---
# <a name="compiler-error-c3536"></a>Chyba kompilátoru C3536

symbol: nejde použít dřív, než se inicializuje.

Uvedený symbol nelze použít před inicializací. V praxi to znamená, že proměnnou nelze použít k inicializaci samotného.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Neinicializujte proměnnou se sebou samým.

## <a name="example"></a>Příklad

Následující příklad vrátí C3536, protože každá proměnná je inicializována se sebou samým.

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)
