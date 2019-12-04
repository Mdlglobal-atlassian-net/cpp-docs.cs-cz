---
title: Chyba kompilátoru C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757381"
---
# <a name="compiler-error-c3136"></a>Chyba kompilátoru C3136

rozhraní: rozhraní COM může dědit jedině z jiného rozhraní COM, rozhraní není rozhraní COM.

Rozhraní, ke kterému jste použili [atribut rozhraní](../../windows/attributes/interface-attributes.md) , dědí z rozhraní, které není rozhraním com. Rozhraní COM nakonec dědí z `IUnknown`. Jakékoli rozhraní předchází atributem rozhraní je rozhraní modelu COM.

Následující příklad generuje C3136:

```cpp
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
