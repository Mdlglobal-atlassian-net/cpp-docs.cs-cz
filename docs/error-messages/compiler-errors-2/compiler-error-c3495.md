---
title: Chyba kompilátoru C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 1a61d4f2472ef6da8aedcf8a8ef90b70de47d8af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738268"
---
# <a name="compiler-error-c3495"></a>Chyba kompilátoru C3495

var: zachycení lambda musí mít automatické trvání úložiště.

Nemůžete zachytit proměnnou, která nemá automatickou dobu trvání úložiště, například proměnnou, která je označena `static` nebo `extern`.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Nepředávejte `static` ani `extern` proměnnou do seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3495, `static` protože `n` proměnná se zobrazí v seznamu zachycení výrazu lambda:

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)

