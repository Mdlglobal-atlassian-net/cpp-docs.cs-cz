---
title: Chyba kompilátoru C3136 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0439aa157a683065ccf7fff5b5f9d6d4d85e2f12
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054217"
---
# <a name="compiler-error-c3136"></a>Chyba kompilátoru C3136

'rozhraní': rozhraní modelu COM může dědit jedině z jiného rozhraní COM, 'rozhraní' není kompatibilní se rozhraní modelu COM

Rozhraní, ke které jste použili [atribut interface](../../windows/interface-attributes.md) dědí z rozhraní, které není rozhraní COM. Rozhraní modelu COM, takže v konečném důsledku dědí z `IUnknown`. Každé rozhraní, které předchází atribut rozhraní je rozhraní modelu COM.

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