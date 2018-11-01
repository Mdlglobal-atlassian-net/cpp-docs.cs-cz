---
title: Chyba kompilátoru C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: ece70a99477b018f6d7a935911f475e4fb4397cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548002"
---
# <a name="compiler-error-c3493"></a>Chyba kompilátoru C3493

'příkaz var' nejde implicitně zachytit, protože nebyl zadán žádný výchozí režim sběru dat

Zachycení výrazu lambda prázdný, `[]`, určuje, že výraz lambda nemá explicitně nebo implicitně zachytit všechny proměnné.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte výchozí režim sběru dat, nebo

- Explicitně zachytit jednu nebo více proměnných.

## <a name="example"></a>Příklad

Následující příklad generuje C3493, protože upravuje externí proměnné, ale určuje klauzule prázdného záznamu:

```
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3493 tak, že zadáte jako výchozí režim sběru dat podle odkazu.

```
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)