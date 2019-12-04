---
title: Chyba kompilátoru C3890
ms.date: 11/04/2016
f1_keywords:
- C3890
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
ms.openlocfilehash: 8d93afa2ac8e365eff2f9256235b391f561cb977
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736539"
---
# <a name="compiler-error-c3890"></a>Chyba kompilátoru C3890

var: nejde adresovat datový člen literálu (Literal).

Literální datový člen existuje v haldě uvolňování paměti.  Objekt na haldě uvolňování paměti lze přesunout, takže přebírání adresy není užitečné.

Následující ukázka generuje C3890:

```cpp
// C3890.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   int p = &Y1::staticConst;   // C3890
   int p2 = Y1::staticConst;   // OK
}
```
