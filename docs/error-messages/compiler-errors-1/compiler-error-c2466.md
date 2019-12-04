---
title: Chyba kompilátoru C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743819"
---
# <a name="compiler-error-c2466"></a>Chyba kompilátoru C2466

nejde přidělit pole s konstantní velikostí 0.

Pole je přiděleno nebo deklarováno s nulovou velikostí. Konstantní výraz pro velikost pole musí být celé číslo větší než nula. Deklarace pole s nulovým dolním indexem je platná jenom pro člena třídy, struktury nebo sjednocení a jenom s rozšířeními Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)).

Následující ukázka generuje C2466:

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
