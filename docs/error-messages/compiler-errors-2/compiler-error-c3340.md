---
title: Chyba kompilátoru C3340
ms.date: 11/04/2016
f1_keywords:
- C3340
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
ms.openlocfilehash: f4010870b84cbe2b8004eea24ab7735839b8c82b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753585"
---
# <a name="compiler-error-c3340"></a>Chyba kompilátoru C3340

Interface: rozhraní nemůže být typu Restricted i default v coclass Class.

Atribut [s omezením](../../windows/restricted.md) a [výchozí](../../windows/default-cpp.md) atribut se vzájemně vylučují.

Následující ukázka generuje C3340:

```cpp
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
