---
title: Upozornění linkerů LNK4217
ms.date: 11/04/2016
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 12766241832d39f0b47ed85036c0ebeb0447fc75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448045"
---
# <a name="linker-tools-warning-lnk4217"></a>Upozornění linkerů LNK4217

lokálně definovaný symbol 'symbol' funkce 'function' byla naimportována

[__declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro symbol, i když je definován symbol místně. Odeberte `__declspec` modifikátor, chcete-li vyřešit tato upozornění.

`symbol` je název symbolu, který je definován v obrázku. `function` je funkce, která importuje symbolu.

Toto upozornění se nezobrazí při kompilaci pomocí volby [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

LNK4217 může také dojít, pokud při pokusu o propojení dvou modulů, když místo toho byste měli kompilovat druhý modul s importovanou knihovnou modulu první.

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

a pak,

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

Pokus o propojení těchto dvou modulů za následek LNK4217, kompilace druhý vzorek s importovanou knihovnou první ukázkové řešení.