---
title: Chyba kompilátoru C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 1719e9f1d3328be083f745498e6f4ad772b0b52a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755236"
---
# <a name="compiler-error-c3481"></a>Chyba kompilátoru C3481

var: nebyla nalezena proměnná zachycení lambda.

Kompilátor nemůže najít definici proměnné, kterou jste předali do seznamu zachycení výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte proměnnou ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3481, protože proměnná `n` není definována:

```cpp
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
