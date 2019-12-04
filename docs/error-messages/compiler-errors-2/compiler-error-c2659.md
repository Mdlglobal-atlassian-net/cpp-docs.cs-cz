---
title: Chyba kompilátoru C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 818d4e63278bc07fad9290dc0c7d4685886bdce6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756068"
---
# <a name="compiler-error-c2659"></a>Chyba kompilátoru C2659

Operátor: funkce jako levý operand

Funkce byla na levé straně zadaného operátoru. Nejčastější příčinou této chyby je, že kompilátor analyzoval identifikátor na levé straně operátoru jako funkci, ale vývojář chtěl, aby to byla proměnná. Další informace najdete v článku Wikipedii [Vexing Analyze](https://en.wikipedia.org/wiki/Most_vexing_parse). Tento příklad ukazuje deklaraci funkce a definici proměnné, které lze snadno zaměnit:

```cpp
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

```cpp
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
