---
title: Kompilátor upozornění (úrovně 1 a 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: 3678d0ce5d9eb9568f0272da4173e72502b0557f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655829"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Kompilátor upozornění (úrovně 1 a 4) C4112

\#vyžaduje celé číslo mezi 1 a číslo řádku

[#Line](../../preprocessor/hash-line-directive-c-cpp.md) direktiva určuje parametr celé číslo, který je mimo povolený rozsah.

Pokud zadaný parametr je menší než 1, čítač řádku se resetuje na hodnotu 1. Pokud je větší než zadaný parametr *číslo*, což je limit definované kompilátorem, čítač řádku je beze změny. Toto je upozornění úrovně 1 v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění úrovně 4 pomocí rozšíření společnosti Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

Následující ukázka generuje C4112:

```
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```