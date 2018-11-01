---
title: Chyba kompilátoru C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: ca9e2d272a5e9ab8fd69094bc1633dbd6ea2c3e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624692"
---
# <a name="compiler-error-c3498"></a>Chyba kompilátoru C3498

'příkaz var': nejde zachytit proměnnou, která má spravované nebo WinRTtype

Nejde zachytit proměnnou, která obsahuje spravovaný typ nebo typ Windows Runtime ve výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Předejte spravovanou nebo prostředí Windows Runtime proměnné do seznamu parametrů výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3498, protože proměnnou se spravovaným typem se zobrazí v seznamu zachycení výrazu lambda:

```
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3498 předáním spravované proměnné `s` do seznamu parametrů výrazu lambda:

```
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)