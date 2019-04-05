---
title: Chyba kompilátoru C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027553"
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

## <a name="see-also"></a>Viz také:

[Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)