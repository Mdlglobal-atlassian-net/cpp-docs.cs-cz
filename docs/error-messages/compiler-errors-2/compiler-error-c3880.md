---
title: Chyba kompilátoru C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 0b169309db88291f8a83b6d1192787b6396e84a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338464"
---
# <a name="compiler-error-c3880"></a>Chyba kompilátoru C3880

'příkaz var': nelze literální datový člen

Typ [literálu](../../extensions/literal-cpp-component-extensions.md) musí být atribut, nebo kompilace lze převést na jednu z následujících typů:

- celočíselný typ

- odkazy řetězců

- výčtu integrálního typu nebo základního typu

Následující ukázka generuje C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```