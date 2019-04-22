---
title: Chyba kompilátoru C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 1e6c3c502290e88feec89877de7ad791084401cf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023253"
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

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)