---
title: Chyba kompilátoru C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 09080a402767835cda9711c2f0fc4d7c8d787439
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508017"
---
# <a name="compiler-error-c3485"></a>Chyba kompilátoru C3485

definice lambdy nemůže mít cv Qualifier

Nelze použít `const` nebo `volatile` kvalifikátor jako součást definice výraz lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte `const` nebo `volatile` kvalifikátoru v definici výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3485, protože používá `const` kvalifikátor definici výrazu lambda v rámci:

```
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)