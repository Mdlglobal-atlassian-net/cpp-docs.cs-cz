---
title: Chyba kompilátoru C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 67eaa9806dff96783f391c46c890b34e1ceef5a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738411"
---
# <a name="compiler-error-c3489"></a>Chyba kompilátoru C3489

klíčové slovo var je povinné, pokud je výchozí režim sběru podle hodnoty.

Pokud určíte, že výchozí režim sběru pro lambda výraz je podle hodnoty, nelze předat proměnnou hodnotou do klauzule zachycení daného výrazu.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nedávejte explicitně proměnnou do klauzule Capture nebo

- Nezadávejte hodnotu podle hodnoty jako výchozí režim sběru dat.

- Zadejte odkaz podle odkazu jako výchozí režim sběru dat.

- Předat proměnnou odkazem na klauzuli zachycení. (To může změnit chování výrazu lambda.)

## <a name="example"></a>Příklad

Následující příklad generuje proměnnou C3489 `n` se zobrazuje podle hodnoty v klauzuli Capture výrazu lambda, jehož výchozí režim je podle hodnoty:

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje čtyři možná řešení na C3489:

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
