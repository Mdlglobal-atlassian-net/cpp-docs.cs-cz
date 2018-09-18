---
title: Chyba kompilátoru C3485 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3485
dev_langs:
- C++
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db3eee53f23aa2cdc958b63faed11ead302f4b1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060743"
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