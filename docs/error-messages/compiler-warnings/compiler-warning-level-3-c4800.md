---
title: Kompilátor upozornění (úroveň 3) C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636134"
---
# <a name="compiler-warning-level-3-c4800"></a>Kompilátor upozornění (úroveň 3) C4800

> "*typ*': vynucení hodnota logická hodnota"true"nebo"Nepravda"(upozornění ohledně výkonu)

Toto upozornění se vygeneruje, když hodnota, která není `bool` přiřazený nebo převést na typ `bool`. Obvykle se tato zpráva způsoben přirazením `int` proměnné `bool` proměnné kde `int` proměnná obsahuje pouze hodnoty **true** a **false**a může být znova deklarovat jako typ `bool`. Pokud nelze přepsat výraz, který má použít typ `bool`, potom můžete přidat "`!=0`" na výraz, který poskytuje typ výrazu `bool`. Přetypování na typ výrazu `bool` nezakáže upozornění, která je záměrné.

Toto upozornění je generováno již v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C4800 a ukazuje, jak ho opravit:

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```