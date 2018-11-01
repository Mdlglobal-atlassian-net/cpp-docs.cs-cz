---
title: Chyba kompilátoru C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: 73e646c386d5c9b8b43d86ab743989b2525f76a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460928"
---
# <a name="compiler-error-c3467"></a>Chyba kompilátoru C3467

'type': Tento typ už je předaný

Kompilátor nalezena více než jedna deklarace typu dopředného pro stejného typu. Je povolena pouze jedna deklarace podle typu.

Další informace najdete v tématu [předávání typů (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3467.

```
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```