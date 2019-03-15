---
title: Určení knihoven DLL pro odložené načtení
ms.date: 11/04/2016
helpviewer_keywords:
- DELAYLOAD linker option
- delayed loading of DLLs
- delayed loading of DLLs, specifying
- /DELAYLOAD linker option
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
ms.openlocfilehash: 2b6737abd76c03186881e83bbd2bf286be6ffe2f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813224"
---
# <a name="specifying-dlls-to-delay-load"></a>Určení knihoven DLL pro odložené načtení

Můžete určit, které knihovny DLL pro odložené načtení se [/delayload](delayload-delay-load-import.md):`dllname` – možnost linkeru. Pokud nechcete použít vlastní verzi pomocná funkce, je třeba také propojit váš program s delayimp.lib (pro desktopové aplikace) nebo dloadhelper.lib (pro aplikace ze storu).

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

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)
