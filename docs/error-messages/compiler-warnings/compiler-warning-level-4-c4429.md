---
title: Kompilátor upozornění (úroveň 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: d4eb7e7075c7adf418254e748f104a6d57c72741
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596622"
---
# <a name="compiler-warning-level-4-c4429"></a>Kompilátor upozornění (úroveň 4) C4429

je to možné neúplný nebo nesprávně vytvořený universal-character-name

Kompilátor zjistil sekvenci znaků, která může být chybně vytvořený univerzální název znaku. Univerzální název znaku je `\u` za nímž následuje čtyř číslic v šestnáctkové soustavě, nebo `\U` za nímž následuje osm číslic v šestnáctkové soustavě.

Následující ukázka generuje C4429:

```
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```