---
title: Chyba kompilátoru C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c4405eb81911b1081d19d25ba779d24bee8f6d37
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039975"
---
# <a name="compiler-error-c3484"></a>Chyba kompilátoru C3484

očekávalo: ->"před návratový typ

Je nutné zadat `->` před návratový typ výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte `->` před návratovým typem.

## <a name="example"></a>Příklad

Následující příklad generuje C3484:

```
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší tím, že poskytuje C3484 `->` před návratový typ výrazu lambda:

```
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Viz také:

[Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)