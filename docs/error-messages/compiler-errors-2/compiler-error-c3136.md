---
title: Chyba kompilátoru C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501086"
---
# <a name="compiler-error-c3136"></a>Chyba kompilátoru C3136

'rozhraní': rozhraní modelu COM může dědit jedině z jiného rozhraní COM, 'rozhraní' není kompatibilní se rozhraní modelu COM

Rozhraní, ke které jste použili [atribut interface](../../windows/attributes/interface-attributes.md) dědí z rozhraní, které není rozhraní COM. Rozhraní modelu COM, takže v konečném důsledku dědí z `IUnknown`. Každé rozhraní, které předchází atribut rozhraní je rozhraní modelu COM.

Následující příklad generuje C3136:

```
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```