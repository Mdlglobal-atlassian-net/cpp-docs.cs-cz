---
title: Chyba kompilátoru C3358 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3358
dev_langs:
- C++
helpviewer_keywords:
- C3358
ms.assetid: 180b93df-e78f-441a-91fb-1594c681f7f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecb4f4bcdf218d9a017939b7d57aa0452afe52a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026527"
---
# <a name="compiler-error-c3358"></a>Chyba kompilátoru C3358

'symbol': symbol se nenašel

Požadované symbol se nenašel.

Následující ukázka generuje C3358:

```
// C3358.cpp
#define __ATLEVENT_H__ 1   // remove this line to resolve the error
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[event_receiver(com)]
struct A   // C3358
{
   void func();
};

int main()
{
}
```