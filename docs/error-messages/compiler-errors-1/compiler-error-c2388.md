---
title: Chyba kompilátoru C2388 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b6bcec4f5f218a52981a7770f5fa6e600494d9a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114147"
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