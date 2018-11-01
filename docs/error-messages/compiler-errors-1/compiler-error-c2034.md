---
title: Chyba kompilátoru C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: 4b4fe769f78e5f826ba08d4819019210f21f860f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479674"
---
# <a name="compiler-error-c2034"></a>Chyba kompilátoru C2034

'identifier': typ bitového pole je příliš malý počet bitů

Počet bitů v deklaraci bitového pole překračuje velikost základního typu.

Následující ukázka generuje C2034:

```
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

Možná řešení:

```
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```