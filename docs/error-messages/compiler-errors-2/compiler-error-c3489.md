---
title: Chyba kompilátoru C3489 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3489
dev_langs:
- C++
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b1631c9be33204edfa697cb349148d274fe30e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081218"
---
# <a name="compiler-error-c3489"></a>Chyba kompilátoru C3489

'příkaz var' se vyžaduje, pokud výchozí režim sběru je podle hodnoty

Pokud určíte, že je výchozí režim sběru pro výraz lambda podle hodnoty, nemůžete předat proměnnou podle hodnoty klauzuli capture výrazu Tento výraz.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proměnné explicitně nepředávejte klauzuli zachycení, nebo

- Nezadávejte podle hodnoty jako výchozí režim sběru dat, nebo

- Zadejte jako výchozí režim sběru dat podle odkazu nebo

- Předejte proměnnou s odkazem na klauzule zachycení. (To může změnit chování část výrazu lambda.)

## <a name="example"></a>Příklad

Následující příklad generuje C3489 proměnnou `n` se zobrazí hodnota v klauzuli capture výrazu lambda výraz, jehož výchozí režim je podle hodnoty:

```
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje na C3489 čtyři možná řešení:

```
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)