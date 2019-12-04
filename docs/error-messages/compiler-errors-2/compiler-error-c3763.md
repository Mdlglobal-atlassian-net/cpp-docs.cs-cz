---
title: Chyba kompilátoru C3763
ms.date: 11/04/2016
f1_keywords:
- C3763
helpviewer_keywords:
- C3763
ms.assetid: 58b1f079-cd1d-46e0-9431-ea18210106b7
ms.openlocfilehash: 5db0f709bceca82d8d3af2c3220fb61d98c1ba8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757251"
---
# <a name="compiler-error-c3763"></a>Chyba kompilátoru C3763

Typ: možnost retval a out se může vyskytovat jenom u typu na datovém ukazateli.

Atributy [out](../../windows/out-cpp.md) nebo [retval](../../windows/retval.md) se můžou vyskytovat jenom u parametrů typu Pointer. Buď odeberte atribut, nebo nastavte parametr typu Pointer.

Následující ukázka generuje C3763:

```cpp
// C3763.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlplus.h>
#include <atlcom.h>

[ module(name=test) ];

[ dispinterface, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IF84 : IDispatch
{
   [id(0x00000002)]HRESULT m2([out]unsigned char);
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class CF84 : public IF84
{   // C3763
public:
   HRESULT __stdcall m2(unsigned char i)
   {
      return S_OK;
   }
};

int main()
{
}
```
