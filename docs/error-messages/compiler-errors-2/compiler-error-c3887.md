---
title: Chyba kompilátoru C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: 85434cb8daba0db82843c09e2d1bb09d98960272
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777438"
---
# <a name="compiler-error-c3887"></a>Chyba kompilátoru C3887

'příkaz var': inicializátor pro literální datový člen musí být konstantní výraz

A [literálu](../../extensions/literal-cpp-component-extensions.md) datový člen lze inicializovat pouze pomocí konstantních následujícímu výrazu.

Následující ukázka generuje C3887:

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Možná řešení:

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```