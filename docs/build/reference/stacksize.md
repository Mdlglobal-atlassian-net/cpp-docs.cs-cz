---
title: STACKSIZE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9b61febedde1a2647df6312a8588b08c6bdad7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705559"
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