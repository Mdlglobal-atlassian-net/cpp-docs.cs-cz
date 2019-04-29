---
title: Upozornění linkerů LNK4217
ms.date: 04/15/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: f1ea3cd0a8770571ae5c55d29a901c134311550f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410223"
---
# <a name="linker-tools-warning-lnk4217"></a>Upozornění linkerů LNK4217

> symbol '*symbol*'definovaný v'*filename_1.obj*"importovaných pomocí"*filename_2.obj*'ve funkci'*funkce*"

[__declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro symbol, i když je definován symbol v souboru objektu v stejnou bitovou kopii. Odeberte `__declspec(dllimport)` modifikátor, chcete-li vyřešit tato upozornění.

## <a name="remarks"></a>Poznámky

*symbol* je název symbolu, který je definován v obrázku. *funkce* je funkce, která importuje symbolu.

Toto upozornění nezobrazí při kompilaci pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost.

LNK4217 může také dojít, pokud při pokusu o propojení dvou modulů, když místo toho byste měli kompilovat druhý modul s importovanou knihovnou modulu první.

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

a pak,

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

LNK4217 způsobí pokus o propojení těchto dvou modulů. Kompilace druhý vzorek s importovanou knihovnou první ukázkové řešení.

## <a name="see-also"></a>Viz také:

[Upozornění Linkerů LNK4049](linker-tools-warning-lnk4049.md) \
[LNK4286 upozornění Linkerů](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)