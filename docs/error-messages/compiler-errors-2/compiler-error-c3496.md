---
title: Chyba kompilátoru C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: c0075bf0e3749966a5e5b9fcd775b5d73171bf17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599417"
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)