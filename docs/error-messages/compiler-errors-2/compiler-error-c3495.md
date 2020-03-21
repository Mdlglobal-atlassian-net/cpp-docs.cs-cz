---
title: Chyba kompilátoru C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 6fe4286142c90f341925d7e76ca8de6d3b7daa9f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075012"
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
