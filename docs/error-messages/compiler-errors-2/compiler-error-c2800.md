---
title: Chyba kompilátoru C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: e893866a28c124e9e6cbc9663a488f89ac2d291b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516893"
---
# <a name="compiler-error-c2800"></a>Chyba kompilátoru C2800

'operator operátor' nemůže být přetížená.

Nemohou být přetíženy následující operátory: přístup ke členům třídy (`.`), ukazatel na člen (`.*`), rozsah rozlišení (`::`), podmíněný výraz (`? :`), a `sizeof`.

Následující ukázka generuje C2800:

```
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```