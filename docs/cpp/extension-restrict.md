---
title: '__restrict: | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d9754f8b0b218fc4d627eb0e27504e8521bf776
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076434"
---
# <a name="restrict"></a>__restrict

Podobně jako **__declspec ( [omezit](../cpp/restrict.md) )** modifikátor, **kvalifikátor __restrict** – klíčové slovo určuje, že symbol nemá v aktuálním oboru alias. **Kvalifikátor __restrict** – klíčové slovo se liší od `__declspec ( restrict )` modifikátor následujícími způsoby:

- **Kvalifikátor __restrict** – klíčové slovo je platný pouze pro proměnné, a `__declspec ( restrict )` je platný jenom pro deklarace a definice funkcí.

- **Kvalifikátor __restrict** je podobný **omezit** od specifikace C99, ale **kvalifikátor __restrict** lze použít v programech jazyka C++ i c.

- Když **kvalifikátor __restrict** se používá, kompilátor nebude šířit vlastnost no-alias proměnné. To znamená Pokud přiřadíte **kvalifikátor __restrict** proměnné non-**kvalifikátor __restrict** proměnné, kompilátor bude stále umožňují jiných __restrict proměnné mít alias. Tím se liší od chování **omezit** – klíčové slovo z dle specifikace C99.

Obecně při ovlivňování chování celé funkce, je vhodnější použít `__declspec ( restrict )` než toto klíčové slovo.

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