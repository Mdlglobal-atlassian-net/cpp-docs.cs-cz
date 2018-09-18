---
title: Chyba kompilátoru C3484 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3484
dev_langs:
- C++
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a79574f85d05c6b1ac32416509ba1f8c05e26b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019183"
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

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)