---
title: Chyba kompilátoru C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c4405eb81911b1081d19d25ba779d24bee8f6d37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381264"
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

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)