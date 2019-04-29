---
title: Chyba kompilátoru C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 3e387fe77c521a4f25ba67205f1fbd552397e272
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381035"
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

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)

