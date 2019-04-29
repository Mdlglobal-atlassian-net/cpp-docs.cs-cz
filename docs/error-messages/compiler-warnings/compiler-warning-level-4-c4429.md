---
title: Kompilátor upozornění (úroveň 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: d4eb7e7075c7adf418254e748f104a6d57c72741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391527"
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