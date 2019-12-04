---
title: Chyba kompilátoru C3488
ms.date: 11/04/2016
f1_keywords:
- C3488
helpviewer_keywords:
- C3488
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
ms.openlocfilehash: 2b69ed4ac8b7e706096d107e9dfaa4447ca1bc79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738424"
---
# <a name="compiler-error-c3488"></a>Chyba kompilátoru C3488

hodnota var není povolená, pokud je výchozí režim sběru podle odkazu.

Pokud určíte, že výchozí režim sběru pro lambda výraz je podle odkazu, nelze předat proměnnou odkazem na klauzuli zachycení daného výrazu.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nedávejte explicitně proměnnou do klauzule Capture nebo

- Nezadávejte odkaz podle odkazu jako výchozí režim sběru dat.

- Jako výchozí režim sběru zadejte hodnotu podle hodnoty nebo

- Předat proměnnou hodnotou do klauzule zachycení. (To může změnit chování výrazu lambda.)

## <a name="example"></a>Příklad

Následující příklad generuje C3488, protože odkaz na proměnnou `n` se zobrazí v klauzuli Capture výrazu lambda, jehož výchozím režimem je odkaz:

```cpp
// C3488a.cpp

int main()
{
   int n = 5;
   [&, &n]() { return n; } (); // C3488
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje čtyři možná řešení na C3488:

```cpp
// C3488b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass &n to the capture clause.
   [&]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-reference as the default capture mode.
   [&n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-value as the default capture mode.
   [=, &n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by value to the capture clause.
   [n]() { return n; } ();
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
