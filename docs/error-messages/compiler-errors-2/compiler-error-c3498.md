---
title: Chyba kompilátoru C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 771e8c72ab4386bb45a11983318f412e784f5bc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738099"
---
# <a name="compiler-error-c3498"></a>Chyba kompilátoru C3498

var: nejde zachytit proměnnou, která má spravovanou nebo WinRTtype.

Nelze zachytit proměnnou, která má spravovaný typ nebo typ prostředí Windows Runtime ve výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Předejte spravovanou nebo prostředí Windows Runtime proměnnou do seznamu parametrů výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3498, protože proměnná, která má spravovaný typ, se zobrazí v seznamu zachycení výrazu lambda:

```cpp
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

Následující příklad vyřeší C3498 předáním spravované proměnné `s` do seznamu parametrů výrazu lambda:

```cpp
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

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
