---
title: Chyba kompilátoru C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 03361fa3e8d4ecb9647d354dd402a9f2b0865eb6
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344678"
---
# <a name="compiler-error-c3541"></a>Chyba kompilátoru C3541

'type': typeid nejde použít na typ, který obsahuje nastavení auto.

[Typeid](../../extensions/typeid-cpp-component-extensions.md) operátor nelze použít pro zadaný typ, protože obsahuje `auto` specifikátor.

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

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../extensions/typeid-cpp-component-extensions.md)