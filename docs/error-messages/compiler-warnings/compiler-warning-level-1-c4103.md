---
title: Kompilátor upozornění (úroveň 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 15d7403d461467e33b7e89957821a311179d33a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577811"
---
# <a name="compiler-warning-level-1-c4103"></a>Kompilátor upozornění (úroveň 1) C4103

'filename': zarovnání změnit po přidání hlavičky, může být kvůli chybějící direktivě #pragma pack(pop).

Balení ovlivňuje rozložení tříd a běžně, pokud balení změny v souborech hlaviček, může dojít k problémům.

Použijte #pragma [pack](../../preprocessor/pack.md)(pop) před ukončením soubor hlaviček, chcete-li vyřešit tato upozornění.

Následující ukázka generuje C4103:

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

a pak,

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```