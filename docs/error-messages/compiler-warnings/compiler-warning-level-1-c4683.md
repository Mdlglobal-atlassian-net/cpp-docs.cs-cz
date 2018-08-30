---
title: Upozornění (úroveň 1) C4683 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a157d3beb7c2efa7f1144a961973652e2ce384f7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194194"
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