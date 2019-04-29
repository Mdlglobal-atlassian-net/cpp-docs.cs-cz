---
title: Chyba kompilátoru C3763
ms.date: 11/04/2016
f1_keywords:
- C3763
helpviewer_keywords:
- C3763
ms.assetid: 58b1f079-cd1d-46e0-9431-ea18210106b7
ms.openlocfilehash: e7dc73334cedda27b82f79b1d2b7a8fc38a8098d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400263"
---
# <a name="compiler-error-c3763"></a>Chyba kompilátoru C3763

'type': "retval" a "out" může vyskytovat jenom u typu ukazatele na data

[Si](../../windows/out-cpp.md) nebo [retval](../../windows/retval.md) atributy lze zobrazit pouze u parametrů typu ukazatele. Buď odeberte atribut, nebo změňte parametr typu ukazatele.

Následující ukázka generuje C3763:

```
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