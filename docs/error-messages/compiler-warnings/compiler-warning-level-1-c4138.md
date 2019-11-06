---
title: Upozornění kompilátoru (úroveň 1) C4138
ms.date: 11/04/2016
f1_keywords:
- C4138
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
ms.openlocfilehash: e6e368f27371b744efa4006630938f68f51a2ca0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627099"
---
# <a name="compiler-warning-level-1-c4138"></a>Upozornění kompilátoru (úroveň 1) C4138

*/se našlo mimo komentář.

Oddělovači koncových komentářů nepředchází znak "otevíracího" komentáře. Kompilátor předpokládá mezeru mezi hvězdičkou (<strong>\*</strong>) a lomítkem (/).

## <a name="example"></a>Příklad

```cpp
// C4138a.cpp
// compile with: /W1
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning
int main()
{
}
```

Toto upozornění může být způsobeno opakováním vnoření komentářů.

Toto upozornění může být vyřešeno, pokud zadáte komentář k oddílům kódu, které obsahují komentáře, uzavřít kód do bloku **#if/#endif** a nastavit kontrolní výraz na hodnotu nula:

```cpp
// C4138b.cpp
// compile with: /W1
#if 0
int my_variable;   /* Declaration currently not needed */
#endif
int main()
{
}
```