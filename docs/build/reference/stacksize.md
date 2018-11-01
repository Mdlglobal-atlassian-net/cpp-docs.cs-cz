---
title: VELIKOST ZÁSOBNÍKU
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597220"
---
# <a name="stacksize"></a>VELIKOST ZÁSOBNÍKU

Nastaví velikost zásobníku v bajtech.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Je ekvivalentní způsob, jak pro zásobníku [přidělení zásobníku](../../build/reference/stack-stack-allocations.md) (/ STACK) – možnost. V dokumentaci na tuto možnost Podrobnosti *rezervovat* a `commit` argumenty.

Tato možnost nemá žádný vliv na knihovnách DLL.

## <a name="see-also"></a>Viz také

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)