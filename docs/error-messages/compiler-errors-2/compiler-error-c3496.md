---
title: Chyba kompilátoru C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738177"
---
# <a name="compiler-error-c3496"></a>Chyba kompilátoru C3496

klíčové slovo this je vždycky zachycené hodnotou: & se ignoruje.

Ukazatel `this` nelze zachytit podle odkazu.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zachytit ukazatel `this` podle hodnoty

## <a name="example"></a>Příklad

Následující příklad generuje C3496, protože odkaz na ukazatel `this` se zobrazí v seznamu zachycení výrazu lambda:

```cpp
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

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
