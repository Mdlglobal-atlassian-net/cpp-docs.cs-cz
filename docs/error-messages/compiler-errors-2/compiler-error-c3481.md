---
title: Chyba kompilátoru C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173356"
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

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)