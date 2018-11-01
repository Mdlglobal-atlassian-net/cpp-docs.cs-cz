---
title: Chyba kompilátoru C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: 1eff84ec133b55ddc3df98364c7d8542be398a69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644168"
---
# <a name="compiler-error-c3340"></a>Chyba kompilátoru C3340

'rozhraní': rozhraní nemůže být "s omezeným přístupem" a "default" v konstruktoru coclass 'class'

[s omezeným přístupem](../../windows/restricted.md) atribut a [výchozí](../../windows/default-cpp.md) atribut se vzájemně vylučují.

Následující ukázka generuje C3340:

```
// C3340.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface
{
   HRESULT f1();
};

[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),
default(IMyIface),
source(IMyIface),restricted(IMyIface) ]
class CmyClass // C3340
{
};

int main()
{
}
```