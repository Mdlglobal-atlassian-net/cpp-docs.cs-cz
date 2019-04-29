---
title: Chyba při vyhodnocování výrazu CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 266e97f28cf0f27cb87e9743399c66aba87c0e8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397104"
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