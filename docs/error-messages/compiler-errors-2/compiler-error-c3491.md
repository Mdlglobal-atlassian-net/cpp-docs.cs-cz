---
title: Chyba kompilátoru C3491 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3491
dev_langs:
- C++
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 64d7b2e4bd602a53afeba2f77293c31bb28902d3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068764"
---
# <a name="compiler-error-c3491"></a>Chyba kompilátoru C3491

'příkaz var': zachycení podle hodnoty nelze upravit ve neměnitelnou výrazu lambda.

Výraz lambda není měnitelný nelze změnit hodnotu proměnné, která je zachycena hodnotou.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Deklarovat výraz lambda `mutable` – klíčové slovo, nebo

- Předejte proměnnou s odkazem na seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3491, protože upravuje hlavní část výrazu lambda není měnitelný zachycená proměnná `m`:

```
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3491 deklarováním výrazu lambda `mutable` – klíčové slovo:

```
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)