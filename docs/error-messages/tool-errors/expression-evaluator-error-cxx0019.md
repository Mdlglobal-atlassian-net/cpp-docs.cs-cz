---
title: Vyhodnocování výrazu CXX0019 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fba76b75c640917b3b99cd41500d682cb1b32f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031805"
---
# <a name="expression-evaluator-error-cxx0019"></a>Chyba při vyhodnocování výrazu CXX0019

Chybný typ přetypování

Chyba při vyhodnocování výrazů C nelze provést přetypování, jak je uvedená typu.

Tato chyba se shoduje s CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Zadaný typ neznámý.

1. Došlo k příliš mnoho úrovní typy ukazatelů. Například přetypování typu

    ```
    (char **)h_message
    ```

     nejde vyhodnotit ve vyhodnocovací filtr výrazů C.