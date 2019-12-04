---
title: Chyba kompilátoru C2586
ms.date: 11/04/2016
f1_keywords:
- C2586
helpviewer_keywords:
- C2586
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
ms.openlocfilehash: be98f475bdcfb4dfdd7f7f37d78f4977d71c52b1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755418"
---
# <a name="compiler-error-c2586"></a>Chyba kompilátoru C2586

Nesprávná syntaxe uživatelsky definovaného převodu: neplatné indirekce

Nepřímý odkaz operátora převodu není povolený.

Následující ukázka generuje C2586:

```cpp
// c2586.cpp
// compile with: /c
struct C {
   * operator int();   // C2586
   operator char();   // OK
};
```
