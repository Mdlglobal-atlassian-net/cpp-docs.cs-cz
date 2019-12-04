---
title: Chyba kompilátoru C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: 178d1221886dc62edd9785d211e2189fa50962f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738294"
---
# <a name="compiler-error-c3493"></a>Chyba kompilátoru C3493

var nejde implicitně zachytit, protože není zadaný žádný výchozí režim zachycení.

Prázdný zachycení výrazu lambda, `[]`, určuje, že lambda výraz neexplicitně nebo implicitně zachytává žádné proměnné.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte výchozí režim sběru dat nebo

- Explicitně zachytit jednu nebo více proměnných.

## <a name="example"></a>Příklad

Následující příklad generuje C3493, protože upravuje externí proměnnou, ale určuje prázdnou klauzuli zachycení:

```cpp
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>Příklad

Následující příklad vyřeší C3493 zadáním odkazu jako výchozího režimu sběru.

```cpp
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
