---
title: Použití polí (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
ms.openlocfilehash: 7f7a987a2b4c18e59dd058ccfc4375c304188398
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575510"
---
# <a name="using-arrays-c"></a>Použití polí (C++)

Můžete přistupovat k jednotlivým prvkům pole pomocí operátoru dolního indexu pole (`[ ]`). Pokud je jednorozměrné pole použito ve výrazu, který nemá žádný index, název pole vyhodnotí ukazatel na první prvek v poli.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Při použití vícedimenzionálních polí můžete použít různé kombinace ve výrazech.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

V předchozím kódu `multi` je trojrozměrné pole typu **double**. `p2multi` Ukazatel odkazuje na pole typu **double** o velikosti tři. V tomto příkladu se používá pole s jeden, dva a třemi dolními indexy. Ačkoli je běžnější určit všechny dolní indexy, stejně jako `cout` příkaz, je někdy užitečné vybrat určitou podmnožinu prvků pole, jak je znázorněno v příkazech, které následují `cout`.

## <a name="see-also"></a>Viz také:

[Pole](../cpp/arrays-cpp.md)