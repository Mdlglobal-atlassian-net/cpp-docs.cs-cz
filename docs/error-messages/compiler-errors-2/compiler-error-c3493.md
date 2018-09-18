---
title: Chyba kompilátoru C3493 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad3c46117e77d432af27321165f1e1ab93d2ef3c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045104"
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