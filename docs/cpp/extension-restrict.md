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
ms.openlocfilehash: 27ac76251456d9a0bf5908ad6d1fc2bee7534e9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360819"
---
# <a name="__restrict"></a>__restrict

Podobně jako modifikátor **__declspec ( [omezit)](../cpp/restrict.md) ** **__restrict** klíčové slovo označuje, že symbol není v aktuálním oboru aliasován. Klíčové slovo **__restrict** se `__declspec ( restrict )` liší od modifikátoru následujícími způsoby:

- Klíčové slovo **__restrict** je platné pouze `__declspec ( restrict )` pro proměnné a je platné pouze pro deklarace funkcí a definice.

- **__restrict** je podobné **omezit** z C99 spec, ale **__restrict** lze použít v c++ nebo C programy.

- Při **použití __restrict** kompilátor nebude šířit vlastnost no-alias proměnné. To znamená, že pokud přiřadíte **proměnnou __restrict** proměnné bez **__restrict,** kompilátor stále povolí aliasní proměnnou bez __restrict. To se liší od chování **omezení** klíčovéslovo z specifikace C99.

Obecně platí, že pokud ovlivníte chování celé funkce, je lepší použít `__declspec ( restrict )` než klíčové slovo.

Pro kompatibilitu s předchozími verzemi je **_restrict** synonymem pro **__restrict** pokud není zadána možnost kompilátoru [/Za \(Zakázat rozšíření jazyka).](../build/reference/za-ze-disable-language-extensions.md)

V sadě Visual Studio 2015 a novější **__restrict** lze použít na odkazy jazyka C++.

> [!NOTE]
> Při použití na proměnnou, která má také [volatile](../cpp/volatile-cpp.md) klíčové slovo, **volatile** bude mít přednost.

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

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
