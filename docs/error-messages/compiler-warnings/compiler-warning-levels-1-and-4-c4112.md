---
title: Upozornění kompilátoru (úrovně 1 a 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: f614373e1b96de2c8167d7981c0a87a4e1c58435
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991239"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Upozornění kompilátoru (úrovně 1 a 4) C4112

\#čára vyžaduje celé číslo mezi 1 a číslem.

Direktiva [#line](../../preprocessor/hash-line-directive-c-cpp.md) určuje celočíselný parametr, který je mimo povolený rozsah.

Pokud je zadaný parametr menší než 1, je čítač řádku obnoven na hodnotu 1. Pokud je zadaný parametr větší než *číslo*, což je limit definovaný kompilátorem, čítač řádku je beze změny. Toto je upozornění úrovně 1 v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění úrovně 4 s rozšířeními Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

Následující ukázka generuje C4112:

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```
