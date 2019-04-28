---
title: Chyba kompilátoru C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: b8b6493b01ac2b88ea50ba50157328f59fdbedf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360382"
---
# <a name="compiler-error-c2659"></a>Chyba kompilátoru C2659

Operátor: funkce jako levý operand

Funkce byla na levé straně zadaného operátoru. Nejčastější příčinou této chyby je, že kompilátor analyzoval identifikátor na levé straně operátoru jako funkci, ale vývojář chtěl, aby to byla proměnná. Další informace najdete v tématu Wikipedia článku [nejobtížnějších analýzy](http://en.wikipedia.org/wiki/Most_vexing_parse). Tento příklad ukazuje deklaraci funkce a definici proměnné, které lze snadno zaměnit:

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

Chcete-li tento problém vyřešit, změňte deklaraci identifikátoru tak, aby nebyl analyzován jako deklarace funkce.

Chyba C2659 se může zobrazit také v případě, že funkce má typ, který nelze použít ve výrazu na levé straně zadaného operátoru. Tento příklad vygeneruje chybu C2659, když kód funkci přiřadí ukazatel na funkci:

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```