---
title: Kompilátor upozornění (úroveň 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: 96f8915b9bec166496ca4305d796ce8ef514ca15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402525"
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