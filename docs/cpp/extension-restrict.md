---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454545"
---
# <a name="restrict"></a>__restrict

Podobně jako **__declspec ( [omezit](../cpp/restrict.md) )** modifikátor, **kvalifikátor __restrict** – klíčové slovo určuje, že symbol nemá v aktuálním oboru alias. **Kvalifikátor __restrict** – klíčové slovo se liší od `__declspec ( restrict )` modifikátor následujícími způsoby:

- **Kvalifikátor __restrict** – klíčové slovo je platný pouze pro proměnné, a `__declspec ( restrict )` je platný jenom pro deklarace a definice funkcí.

- **Kvalifikátor __restrict** je podobný **omezit** od specifikace C99, ale **kvalifikátor __restrict** lze použít v programech jazyka C++ i c.

- Když **kvalifikátor __restrict** se používá, kompilátor nebude šířit vlastnost no-alias proměnné. To znamená Pokud přiřadíte **kvalifikátor __restrict** proměnné non-**kvalifikátor __restrict** proměnné, kompilátor bude stále umožňují jiných __restrict proměnné mít alias. Tím se liší od chování **omezit** – klíčové slovo z dle specifikace C99.

Obecně při ovlivňování chování celé funkce, je vhodnější použít `__declspec ( restrict )` než toto klíčové slovo.

Z důvodu kompatibility s předchozími verzemi **_restrict** je synonymum pro **kvalifikátor __restrict** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

V sadě Visual Studio 2015 a novější **kvalifikátor __restrict** lze použít v referencích C++.

> [!NOTE]
>  Při použití na proměnnou, která má také [volatile](../cpp/volatile-cpp.md) – klíčové slovo, **volatile** bude mít přednost.

## <a name="example"></a>Příklad

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)