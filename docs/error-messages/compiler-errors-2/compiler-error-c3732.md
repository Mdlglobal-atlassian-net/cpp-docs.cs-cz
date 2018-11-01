---
title: Chyba kompilátoru C3732
ms.date: 11/04/2016
f1_keywords:
- C3732
helpviewer_keywords:
- C3732
ms.assetid: 2d55a7e1-9c39-4379-a093-2f7beb27e2ca
ms.openlocfilehash: c71cca3643f6337060de6e4bb56ac64d8f0d6e4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611351"
---
# <a name="compiler-error-c3732"></a>Chyba kompilátoru C3732

'rozhraní': vlastní rozhraní, které aktivuje události COM nemůže dědit od rozhraní IDispatch

Nelze zdědit rozhraní, které podporuje události COM `IDispatch`. Další informace najdete v tématu [zpracování událostí v modulu COM](../../cpp/event-handling-in-com.md).

Generuje následující chybu C3732:

```
// C3732.cpp
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[module(name="test")];

// to resolve this C3732, use dual instead of object
// or inherit from IUnknown
[ object ]
__interface I : IDispatch
{
};

[ event_source(com), coclass ]
struct A
{
   __event __interface I;   // C3732
};

int main()
{
}
```