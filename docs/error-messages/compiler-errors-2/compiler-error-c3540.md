---
title: Chyba kompilátoru C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037166"
---
# <a name="compiler-error-c3540"></a>Chyba kompilátoru C3540

'type': operátor sizeof: nelze použít pro typ, který obsahuje nastavení auto.

[Sizeof](../../cpp/sizeof-operator.md) operátor nelze použít pro zadaný typ, protože obsahuje `auto` specifikátor.

## <a name="example"></a>Příklad

Následující příklad provede C3540.

```
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

[auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof – operátor](../../cpp/sizeof-operator.md)