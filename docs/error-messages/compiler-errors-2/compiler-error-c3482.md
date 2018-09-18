---
title: Chyba kompilátoru C3482 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3482
dev_langs:
- C++
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9921c25575888ab2db1c092f9325002d1becb921
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053372"
---
# <a name="compiler-error-c3482"></a>Chyba kompilátoru C3482

"this" jde použít jenom jako zachycení lambdy v rámci funkce nestatického člena

Nelze předat `this` na seznamu zachycení výrazu lambda, který je deklarován v statickou metodu nebo globálními funkcemi.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Převést na nestatické metody nadřazené funkce nebo

- Odeberte `this` ukazatele v seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3482:

```
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)