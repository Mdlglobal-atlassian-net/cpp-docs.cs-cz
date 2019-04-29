---
title: Chyba kompilátoru C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 62afcb1fafc19d3d61a86f2fbc10cb99e095afc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393659"
---
# <a name="compiler-error-c2388"></a>Chyba kompilátoru C2388

'symbol': symbol nejde deklarovat s obě možnosti __declspec(appdomain) a \__declspec(process)

`appdomain` a `process` `__declspec` Modifikátory nelze použít u stejného symbolu. Úložiště pro proměnnou existuje proces nebo doménu aplikace.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [procesu](../../cpp/process.md).

Následující ukázka generuje C2388:

```
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```