---
title: Kompilátor upozornění (úroveň 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 287465e9a3f5681f459f0823a4409b0906309a55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436547"
---
# <a name="compiler-warning-level-1-c4096"></a>Kompilátor upozornění (úroveň 1) C4096

'a': rozhraní není rozhraní COM; nebude se emitovat do IDL

Definice rozhraní, který vám může mít určený jako rozhraní modelu COM nebyl definován jako rozhraní modelu COM a proto nebude se emitovat do souboru IDL.

Zobrazit [atributy rozhraní](../../windows/attributes/interface-attributes.md) pro seznam atributů, které je rozhraní modelu COM rozhraní.

Následující ukázka generuje C4096:

```
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```