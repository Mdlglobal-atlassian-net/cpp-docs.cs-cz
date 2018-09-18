---
title: Chyba kompilátoru C3480 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3480
dev_langs:
- C++
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd58a8c38ee6dc5f77ef280ba3b7a546a666cd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107855"
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