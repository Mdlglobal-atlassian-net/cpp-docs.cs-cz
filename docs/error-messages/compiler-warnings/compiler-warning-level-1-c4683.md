---
title: Upozornění kompilátoru (úroveň 1) C4683
ms.date: 08/27/2018
f1_keywords:
- C4683
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
ms.openlocfilehash: f86cf8f6d894d6efaa1b49977634956dc1979a98
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175426"
---
# <a name="compiler-warning-level-1-c4683"></a>Upozornění kompilátoru (úroveň 1) C4683

> '*Function*': zdroj události má parametr ' out'-Parameter; cvičení opatrnosti při zapojení více obslužných rutin událostí

## <a name="remarks"></a>Poznámky

Pokud se zdroji událostí modelu COM naslouchá více než jedna jímka události, hodnota parametru out může být ignorována.

Počítejte s tím, že v následujících situacích dojde k nevrácení paměti:

1. Má-li metoda výstupní parametr, který je interně přidělen, například BSTR *.

2. Má-li událost více než jednu obslužnou rutinu (Jedná se o událost vícesměrového vysílání).

Důvodem nevracení je to, že výstupní parametr bude nastaven více než jednou obslužnou rutinou, ale vrátí se na web volání pouze pomocí poslední obslužné rutiny.

## <a name="example"></a>Příklad

Následující ukázka generuje C4683 a ukazuje, jak ji opravit:

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
