---
title: Upozornění (úroveň 1) C4138 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2e637c73482b1a59034d6a269ea2240445bdef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046904"
---
# <a name="compiler-warning-level-1-c4138"></a>Kompilátor upozornění (úroveň 1) C4138

' * / se našlo mimo komentář

Oddělovač komentáře uzavírací není za znakem oddělovače otevírání komentář. Kompilátor předpokládá mezeru mezi hvězdičky (<strong>\*</strong>) a lomítkem (/).

## <a name="example"></a>Příklad

```
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Toto upozornění může být způsobeno pokusu vnořit komentáře.

Toto upozornění může být vyřešen po okomentování sekcí kódu, které obsahují komentáře, uzavřete kód v **#if / #endif** blokovat a nastavte na hodnotu nula řídicí výraz:

```
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```