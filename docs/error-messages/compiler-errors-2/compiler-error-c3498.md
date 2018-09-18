---
title: Chyba kompilátoru C3498 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3498
dev_langs:
- C++
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb87abc113e586aa4f3097444df4c5a46a6a92c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106769"
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