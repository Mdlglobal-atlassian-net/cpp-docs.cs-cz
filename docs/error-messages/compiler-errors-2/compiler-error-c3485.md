---
title: Chyba kompilátoru C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381136"
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

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)