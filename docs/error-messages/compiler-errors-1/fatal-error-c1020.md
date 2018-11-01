---
title: Závažná chyba C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469807"
---
# <a name="fatal-error-c1020"></a>Závažná chyba C1020

neočekávané #endif

`#endif` – Direktiva nemá odpovídající `#if`, `#ifdef`, nebo `#ifndef` směrnice. Být, že každý `#endif` má odpovídající směrnice.

Následující ukázka generuje C1020:

```
// C1020.cpp
#endif     // C1020
```

Možná řešení:

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```