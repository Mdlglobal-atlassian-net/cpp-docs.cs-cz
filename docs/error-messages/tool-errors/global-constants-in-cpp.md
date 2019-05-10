---
title: Globální konstanty v jazyku C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 2f0621f52fe445f8f2058ef902824ddc1f5e2bb5
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856107"
---
# <a name="global-constants-in-c"></a>Globální konstanty v jazyku C++

Globální konstanty jazyka C++ mají statické propojení. To se liší od C. Pokud se pokusíte použít globální konstanty v jazyce C++ ve více souborech získáte nevyřešené externí chyby. Kompilátor optimalizuje globální konstanty, nezbývá místo vyhrazena pro proměnnou.

Jedním ze způsobů pro vyřešení této chyby je zahrnout soubor hlaviček const inicializace a včetně této hlavičky v rámci souborů CPP, pokud je to nezbytné, tak, jako kdyby byla prototypu funkce. Další možností je vytvořit proměnnou, která není konstantní a použití konstantní odkaz při posuzování ho.

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

a pak,

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Viz také:

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)