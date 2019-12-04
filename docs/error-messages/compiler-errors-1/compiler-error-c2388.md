---
title: Chyba kompilátoru C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 21658a659468a6e2a0d911af70eefdaed320446c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745054"
---
# <a name="compiler-error-c2388"></a>Chyba kompilátoru C2388

' symbol ': symbol nemůže být deklarován současně s __declspec (AppDomain) a \__declspec (Process)

Modifikátory `__declspec` `appdomain` a `process` nelze použít na stejný symbol. Úložiště pro proměnnou existuje pro jednotlivé procesy nebo pro doménu aplikace.

Další informace naleznete v tématu [AppDomain](../../cpp/appdomain.md) a [Process](../../cpp/process.md).

Následující ukázka generuje C2388:

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
