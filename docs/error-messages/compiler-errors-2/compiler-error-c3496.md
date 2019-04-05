---
title: Chyba kompilátoru C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026687"
---
# <a name="compiler-error-c3496"></a>Chyba kompilátoru C3496

"this" se vždycky zachycuje na základě hodnoty: & Ignorovat

Nelze zachytit `this` ukazatelem, odkazem.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zachycení `this` ukazatele podle hodnoty.

## <a name="example"></a>Příklad

Následující příklad generuje C3496, protože odkaz na `this` ukazatel se zobrazí v seznamu zachycení výrazu lambda:

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>Viz také:

[Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)