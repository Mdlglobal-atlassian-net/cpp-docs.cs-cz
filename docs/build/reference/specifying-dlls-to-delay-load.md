---
title: Určení knihoven DLL pro odložené načtení
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 986dab0621127c90097808025825930bf9974a7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549861"
---
# <a name="specifying-dlls-to-delay-load"></a>Určení knihoven DLL pro odložené načtení

Můžete určit, které knihovny DLL pro odložené načtení se [/delayload](../../build/reference/delayload-delay-load-import.md):`dllname` – možnost linkeru. Pokud nechcete použít vlastní verzi pomocná funkce, je třeba také propojit váš program s delayimp.lib (pro desktopové aplikace) nebo dloadhelper.lib (pro aplikace ze storu).

Toto je jednoduchý příklad odloženého načítání knihovny DLL:

```
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll
#include <windows.h>
// uncomment these lines to remove .libs from command line
// #pragma comment(lib, "delayimp")
// #pragma comment(lib, "user32")

int main() {
   // user32.dll will load at this point
   MessageBox(NULL, "Hello", "Hello", MB_OK);
}
```

Sestavení verze ladění projektu. Krokovat kód pomocí ladicího programu a můžete si všimnout, že user32.dll je načtena pouze při volání `MessageBox`.

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)