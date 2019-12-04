---
title: Chyba kompilátoru C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: 25dbb8897db45cbddaaf7f0530bcb2a8653b03cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752792"
---
# <a name="compiler-error-c3737"></a>Chyba kompilátoru C3737

Delegate: delegát nesmí mít explicitní konvenci volání.

Nemůžete zadat [konvenci volání](../../cpp/calling-conventions.md) pro `delegate`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3737:

```cpp
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
