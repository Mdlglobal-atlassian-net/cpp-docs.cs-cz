---
title: Chyba kompilátoru C3890
ms.date: 11/04/2016
f1_keywords:
- C3890
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
ms.openlocfilehash: 2354be5ac7299fc0361e1b3ad50554e9949f8c1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385547"
---
# <a name="compiler-error-c3890"></a>Chyba kompilátoru C3890

'příkaz var': Nelze převzít adresu proměnné literální datový člen

Datový člen literal existuje na haldě uvolňování paměti.  Objekt na haldě uvolňování je možné přesunout, takže převzetí adresy není užitečné.

Následující ukázka generuje C3890:

```
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