---
title: VELIKOST ZÁSOBNÍKU
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 5f0c23ad8b8d81f888616042ee5d6ba5bc63bd44
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412871"
---
# <a name="stacksize"></a>VELIKOST ZÁSOBNÍKU

Nastaví velikost zásobníku v bajtech.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Poznámky

Je ekvivalentní způsob, jak pro zásobníku [přidělení zásobníku](../../build/reference/stack-stack-allocations.md) (/ STACK) – možnost. V dokumentaci na tuto možnost Podrobnosti *rezervovat* a `commit` argumenty.

Tato možnost nemá žádný vliv na knihovnách DLL.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](../../build/reference/rules-for-module-definition-statements.md)
