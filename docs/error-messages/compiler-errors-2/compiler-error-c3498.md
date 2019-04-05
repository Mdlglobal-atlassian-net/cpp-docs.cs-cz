---
title: Chyba kompilátoru C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 463e210e5a1ac5eb6d197062ed8921f9bbae4ad2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037880"
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

## <a name="see-also"></a>Viz také:

[Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)