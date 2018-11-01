---
title: Chyba kompilátoru C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 81fcbb8102d5df8059aad00772b7ee0cc07c01d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452465"
---
# <a name="compiler-error-c3495"></a>Chyba kompilátoru C3495

'příkaz var': zachycení lambda musí mít automatickou dobou trvání úložiště

Nejde zachytit proměnnou, která nemá automatickou dobou trvání úložiště, například proměnná, která je označena `static` nebo `extern`.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nepředávejte `static` nebo `extern` proměnné do seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3495 vzhledem k tomu, `static` proměnnou `n` se zobrazí v seznamu zachycení výrazu lambda:

```
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)

