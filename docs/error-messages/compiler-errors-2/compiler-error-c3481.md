---
title: Chyba kompilátoru C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 32a04c2c49f8d9d974c3423756c4c9fc59a46495
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661978"
---
# <a name="compiler-error-c3481"></a>Chyba kompilátoru C3481

'příkaz var': proměnná zachycení lambda nebyl nalezen

Kompilátor nemůže najít definice proměnné, kterou jste předali do seznamu zachycení výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proměnnou můžete odeberte ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3481 protože proměnné `n` není definován:

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)