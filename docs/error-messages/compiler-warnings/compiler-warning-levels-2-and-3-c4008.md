---
title: Kompilátor upozornění (úrovně 2 a 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604084"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Kompilátor upozornění (úrovně 2 a 3) C4008

'identifier': atribut ' attribute ' ignorovat

Kompilátor ignoruje `__fastcall`, **statické**, nebo **vložené** atribut – funkce (upozornění úrovně 3) nebo data (upozornění úrovně 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. `__fastcall` atribut s daty.

1. **statické** nebo **vložené** atributem **hlavní** funkce.