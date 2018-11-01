---
title: Chyba kompilátoru C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 8a1525539c84ea427815a03057bb6d2f9213fec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431107"
---
# <a name="compiler-error-c3707"></a>Chyba kompilátoru C3707

'function': metoda dispinterface musí mít dispid

Pokud používáte `dispinterface` metoda, je nutné ji přiřadit `dispid`. Chcete-li tuto chybu opravit, přiřaďte `dispid` k `dispinterface` metody, například podle odstraňuje se komentování `id` atributu v metodě v následující ukázce. Další informace najdete v tématu atributy [dispinterface](../../windows/dispinterface.md) a [id](../../windows/id.md).

Následující ukázka generuje C3707:

```
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```