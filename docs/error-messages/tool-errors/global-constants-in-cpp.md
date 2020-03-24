---
title: Globální konstanty v jazyku C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: cabe5e92a496181d60536d7274eca388aba5c068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195471"
---
# <a name="global-constants-in-c"></a>Globální konstanty v jazyku C++

C++globální konstanty mají statické propojení. To se liší od jazyka C. Pokud se pokusíte použít globální konstantu v C++ v několika souborech, získáte nevyřešenou externí chybu. Kompilátor optimalizuje globální konstanty a zachová místo vyhrazené pro proměnnou.

Jedním ze způsobů, jak tuto chybu vyřešit, je zahrnout inicializace const do hlavičkového souboru a zahrnout tuto hlavičku do souborů CPP v případě potřeby, stejně jako v případě prototypu funkce. Další možností je nastavit proměnnou jako nekonstantní a použít konstantní odkaz při jejich vyhodnocování.

Následující ukázka generuje C2019:

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

a potom

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Viz také

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
