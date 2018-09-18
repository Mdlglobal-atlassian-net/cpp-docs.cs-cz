---
title: Chyba kompilátoru C3495 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dda1e2f2699969ad0bc446d9f79a0004e043998d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067386"
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


