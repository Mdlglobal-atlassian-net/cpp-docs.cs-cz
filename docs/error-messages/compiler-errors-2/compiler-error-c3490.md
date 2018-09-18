---
title: Chyba kompilátoru C3490 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3490
dev_langs:
- C++
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 503302d323f45b5f7c3971803fef0547ff28e0c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077695"
---
# <a name="compiler-error-c3490"></a>Chyba kompilátoru C3490

'příkaz var' nelze změnit, protože se přistupuje prostřednictvím objektu const.

Výraz lambda, který je deklarován v `const` metoda nemůže měnit data neměnitelnou člena.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte `const` modifikátor z vaší deklarace metody.

## <a name="example"></a>Příklad

Následující příklad generuje C3490, protože upravuje členskou proměnnou `_i` v `const` metody:

```
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3490 odebráním `const` modifikátor od deklarace metody:

```
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)