---
title: Kompilátor upozornění (úroveň 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: 264753ece6cbabded21df8e6b9dbb463f811e8a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375155"
---
# <a name="compiler-warning-level-1-c4683"></a>Kompilátor upozornění (úroveň 1) C4683

> "*funkce*': Zdroj události má"out"-parametr; postupujte obezřetně při připojení více obslužných rutin událostí

## <a name="remarks"></a>Poznámky

Pokud více než jeden jímky událostí naslouchá ke zdroji událostí modelu COM, může být hodnota výstupní parametr ignorován.

Mějte na paměti, že dojde k nevracení paměti v následujících situacích:

1. Pokud metoda má výstupní parametr, který je interně přidělen, například BSTR *.

2. Pokud má více než jednu obslužnou rutinu události (je vícesměrového vysílání událostí).

Důvod nevracení paměti je, že výstupní parametr bude možné nastavit více než jeden obslužnou rutinou, ale vrácené na lokalitu volání pouze poslední obslužnou rutinou.

## <a name="example"></a>Příklad

Následující ukázka generuje C4683 a ukazuje, jak ho opravit:

```cpp
// C4683.cpp
// compile with: /W1 /LD
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="xx") ];

[ object ]
__interface I {
   HRESULT f([out] int* pi);
   // try the following line instead
   // HRESULT f(int* pi);
};

[ coclass, event_source(com) ]
struct E {
   __event __interface I;   // C4683
};
```