---
title: Chyba kompilátoru C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528123"
---
# <a name="compiler-error-c2289"></a>Chyba kompilátoru C2289

stejný typ kvalifikátor použít víc než jednou

Typ deklarace nebo definice používá kvalifikátor typu (`const`, `volatile`, `signed`, nebo `unsigned`) více než jednou, což způsobuje chybu podle kompatibility ANSI (**/Za**).

Následující ukázka generuje C2286:

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```