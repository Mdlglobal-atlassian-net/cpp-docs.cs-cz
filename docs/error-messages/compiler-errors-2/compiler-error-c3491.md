---
title: Chyba kompilátoru C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: 78f90ee1c44a0d42e529a027b1e7fc90a0da3cdb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738320"
---
# <a name="compiler-error-c3491"></a>Chyba kompilátoru C3491

var: zachycení po hodnotě nejde upravovat v neměnitelném výrazu lambda.

Výraz lambda, který není proměnlivý, nemůže změnit hodnotu proměnné, která je zachycena hodnotou.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Deklarujte výraz lambda pomocí klíčového slova `mutable` nebo

- Předat proměnnou odkazem na seznam zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3491, protože tělo neměnitelného výrazu lambda upravuje proměnnou zachycení `m`:

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Příklad

Následující příklad vyřeší C3491 deklarací výrazu lambda s klíčovým slovem `mutable`:

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
