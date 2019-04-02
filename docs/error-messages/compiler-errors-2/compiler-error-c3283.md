---
title: Chyba kompilátoru C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: 593b04b8593e261aa1980ada7693300b52a869c5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779986"
---
# <a name="compiler-error-c3283"></a>Chyba kompilátoru C3283

'type': rozhraní nemůže mít konstruktor instance

Modul CLR [rozhraní](../../extensions/interface-class-cpp-component-extensions.md) nemůže mít konstruktor instance.  Statický konstruktor je povolen.

Následující ukázka generuje C3283:

```
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

Možná řešení:

```
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```