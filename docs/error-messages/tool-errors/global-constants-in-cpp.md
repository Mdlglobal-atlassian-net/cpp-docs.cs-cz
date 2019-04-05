---
title: Globální konstanty v jazyku C++
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 1ae29b8744e24b6471f0d5536f3f13cc5ae59499
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030190"
---
# <a name="global-constants-in-c"></a>Globální konstanty v jazyku C++

Globální konstanty jazyka C++ mají statické propojení. To se liší od C. Pokud se pokusíte použít globální konstanty v jazyce C++ ve více souborech získáte nevyřešené externí chyby. Kompilátor optimalizuje globální konstanty, nezbývá místo vyhrazena pro proměnnou.

Jedním ze způsobů pro vyřešení této chyby je zahrnout soubor hlaviček const inicializace a včetně této hlavičky v rámci souborů CPP, pokud je to nezbytné, tak, jako kdyby byla prototypu funkce. Další možností je vytvořit proměnnou, která není konstantní a použití konstantní odkaz při posuzování ho.

Následující ukázka generuje C2019:

```
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

a pak,

```
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>Viz také:

[Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)