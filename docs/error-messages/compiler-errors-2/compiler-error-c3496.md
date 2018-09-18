---
title: Chyba kompilátoru C3496 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec4602e6a0061f5eb750ab29587209a6c97985d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062290"
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