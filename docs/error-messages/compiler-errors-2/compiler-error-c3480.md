---
title: Chyba kompilátoru C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: b856f607d764ac0a42781a80787663d965748317
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626899"
---
# <a name="compiler-error-c3480"></a>Chyba kompilátoru C3480

'příkaz var': proměnná zachycení lambda musí být z nadřazeného oboru – funkce

Proměnná zachycení lambda není v ohraničujícím oboru funkce.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proměnnou můžete odeberte ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3480, protože proměnná `global` nepochází z nadřazeného oboru funkce:

```
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Příklad

V následujícím příkladu řeší C3480 odebráním proměnné `global` ze seznamu zachycení výrazu lambda:

```
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)