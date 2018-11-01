---
title: Chyba kompilátoru C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 356936ee09b75b6930840e015d00ccebb2fd8bc2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596375"
---
# <a name="compiler-error-c3541"></a>Chyba kompilátoru C3541

'type': typeid nejde použít na typ, který obsahuje nastavení auto.

[Typeid](../../windows/typeid-cpp-component-extensions.md) operátor nelze použít pro zadaný typ, protože obsahuje `auto` specifikátor.

## <a name="example"></a>Příklad

Následující příklad provede C3541.

```
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[identifikátor TypeId.](../../windows/typeid-cpp-component-extensions.md)