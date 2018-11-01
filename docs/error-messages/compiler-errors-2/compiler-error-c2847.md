---
title: Chyba kompilátoru C2847
ms.date: 11/04/2016
f1_keywords:
- C2847
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
ms.openlocfilehash: 99c49be746cea6fb80c5e24667bcd97556a0ad04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481481"
---
# <a name="compiler-error-c2847"></a>Chyba kompilátoru C2847

nelze použít operátor sizeof: spravované nebo typ WinRT 'class'

[Sizeof](../../cpp/sizeof-operator.md) operátor získá hodnotu objektu v době kompilace. Velikost spravované nebo třída WinRT, rozhraní nebo hodnotového typu je dynamický a nemůže být znám v době kompilace.

Například následující ukázka generuje C2847:

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
