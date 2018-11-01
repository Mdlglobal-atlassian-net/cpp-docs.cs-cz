---
title: Chyba kompilátoru C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 915217ffbe848b2814e9960183854e09a80b9ee8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434850"
---
# <a name="compiler-error-c2448"></a>Chyba kompilátoru C2448

'identifier': inicializátor function-style se zdá být definicí funkce.

Definice funkce je nesprávný.

Tuto chybu může způsobovat formální seznam ve starém stylu jazyka C.

Následující ukázka generuje C2448:

```
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```