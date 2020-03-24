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
ms.openlocfilehash: cb340554bc20516175400c4d14a5d0dba934a313
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188958"
---
# <a name="__restrict"></a>__restrict

Podobně jako u modifikátoru **__declspec ( [omezit](../cpp/restrict.md) )** označuje klíčové slovo **__restrict** , že v aktuálním oboru není uveden alias. Klíčové slovo **__restrict** se od modifikátoru `__declspec ( restrict )` liší následujícími způsoby:

- Klíčové slovo **__restrict** je platné pouze pro proměnné a `__declspec ( restrict )` je platné pouze pro deklarace a definice funkcí.

- **__restrict** se podobá **omezení** ze specifikace C99, ale **__restrict** je možné použít v programech C++ nebo v C.

- Při použití **__restrict** kompilátor nerozšíří vlastnost No-alias proměnné. To znamená, že pokud přiřadíte **__restrict** proměnnou k proměnné, která není **__restrict** , kompilátor přesto umožní aliasovat proměnnou bez __restrict. To se liší od chování klíčového slova **restrict** ze specifikace C99.

Obecně platí, že pokud máte vliv na chování celé funkce, je lepší použít `__declspec ( restrict )` než klíčové slovo.

Z důvodu kompatibility s předchozími verzemi je **_restrict** synonymem pro **__restrict** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

V aplikaci Visual Studio 2015 a novějších lze **__restrict** použít na C++ odkazech.

> [!NOTE]
>  Při použití pro proměnnou, která má také klíčové slovo [volatile](../cpp/volatile-cpp.md) , bude mít **volatile** přednost.

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
