---
title: Upozornění linkerů LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: fb355b6d004d9488abac89ef44c9ec38c791ffda
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988036"
---
# <a name="linker-tools-warning-lnk4221"></a>Upozornění linkerů LNK4221

Tento soubor objektu nedefinuje žádné dříve nedefinované veřejné symboly, takže ho nebude používat žádná operace propojení, která tuto knihovnu spotřebovává.

Vezměte v úvahu následující dva fragmenty kódu.

```cpp
// a.cpp
#include <atlbase.h>
```

```cpp
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

Chcete-li zkompilovat soubory a vytvořit dva soubory objektů, spusťte na příkazovém řádku soubor **CL/c a. cpp b. cpp** . Pokud propojíte soubory objektů spuštěním **odkazu/lib/out: test. lib a. obj b. obj**, zobrazí se Upozornění linkerů LNK4221. Pokud propojíte objekty spuštěním **odkazu/lib/out: test. lib b. obj a. obj**, nebudete dostávat žádné upozornění.

V druhém scénáři není vydáno žádné upozornění, protože linker funguje v rámci prvního nebo posledního použití metody LIFO. V prvním scénáři je b. obj zpracován před objektem. obj a. obj nemá žádné nové symboly pro přidání. Tím, že dáte pokyn linkeru ke zpracování. obj, můžete se vyhnout upozornění.

::: moniker range=">=vs-2019"

Obvyklou příčinou této chyby je, že dva zdrojové soubory určují možnost [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) se stejným názvem souboru hlaviček, který je zadaný v poli **Předkompilovaná hlavička** . Obvyklou příčinou tohoto problému je soubor *PCH. h* , protože ve výchozím nastavení soubor *PCH. cpp* obsahuje soubor *PCH. h* a nepřidává žádné nové symboly. Pokud jiný zdrojový soubor obsahuje *PCH. h* s **/YC** a přidružený soubor. obj je zpracován před souborem PCH. obj, linker vyvolá linkerů LNK4221.

::: moniker-end

::: moniker range="<=vs-2017"

Obvyklou příčinou této chyby je, že dva zdrojové soubory určují možnost [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) se stejným názvem souboru hlaviček, který je zadaný v poli **Předkompilovaná hlavička** . Obvyklou příčinou tohoto problému je soubor stdafx *. h* , protože ve výchozím nastavení obsahuje *stdafx* *. h a* nepřidává žádné nové symboly. Pokud jiný zdrojový soubor obsahuje *stdafx. h* s **/YC** a přidružený soubor. obj je zpracován před stdafx. obj, linker vyvolá linkerů LNK4221.

::: moniker-end

Jedním ze způsobů, jak tento problém vyřešit, je ujistit se, že pro každou předkompilovanou hlavičku je k dispozici pouze jeden zdrojový soubor, který obsahuje **/YC**. Všechny ostatní zdrojové soubory musí používat předkompilované hlavičky. Další informace o tom, jak změnit toto nastavení, naleznete v tématu [/Yu (použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md).
