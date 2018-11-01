---
title: Chyba kompilátoru C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526326"
---
# <a name="compiler-error-c2466"></a>Chyba kompilátoru C2466

nejde přidělit pole s konstantní velikostí 0

Pole je přidělena nebo deklarované s nulovou velikostí. Konstantní výraz pro velikost pole musí být celé číslo větší než nula. Deklarace pole s nulovou dolní index je platný pouze pro třídy, struktury nebo člen sjednocení a pouze s rozšířeními společnosti Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

Následující ukázka generuje C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```