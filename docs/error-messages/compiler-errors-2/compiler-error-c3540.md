---
title: Chyba kompilátoru C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 94f35f9f3bf64e09087f28a11a4fb9802d9d3c0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761514"
---
# <a name="compiler-error-c3540"></a>Chyba kompilátoru C3540

' type ': operátor sizeof nelze použít pro typ, který obsahuje ' auto '

Operátor [sizeof](../../cpp/sizeof-operator.md) nelze použít na zadaný typ, protože obsahuje specifikátor `auto`.

## <a name="example"></a>Příklad

Následující příklad vrací C3540.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof – operátor](../../cpp/sizeof-operator.md)
