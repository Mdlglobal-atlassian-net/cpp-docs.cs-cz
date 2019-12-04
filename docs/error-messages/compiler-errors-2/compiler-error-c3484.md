---
title: Chyba kompilátoru C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c9895a3e5a8ae7e941fccde2da85fedfb3d2c6dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743117"
---
# <a name="compiler-error-c3484"></a>Chyba kompilátoru C3484

před návratovým typem se očekávala hodnota->.

Je nutné zadat `->` před návratovým typem výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Zadejte `->` před návratovým typem.

## <a name="example"></a>Příklad

Následující příklad generuje C3484:

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>Příklad

Následující příklad řeší C3484 poskytnutím `->` před návratovým typem výrazu lambda:

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
