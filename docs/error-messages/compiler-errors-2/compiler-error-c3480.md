---
title: Chyba kompilátoru C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 255fb12d587a94aac798814736f0b26770f608b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760475"
---
# <a name="compiler-error-c3480"></a>Chyba kompilátoru C3480

var: proměnná zachycení lambda musí být z oboru ohraničující funkce.

Zachycená proměnná lambda není z oboru ohraničující funkce.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Odeberte proměnnou ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad vygeneruje C3480, protože proměnná `global` nepochází z oboru ohraničující funkce:

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>Příklad

Následující příklad vyřeší C3480 odebráním proměnné `global` ze seznamu zachycení výrazu lambda:

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>Viz také:

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)
