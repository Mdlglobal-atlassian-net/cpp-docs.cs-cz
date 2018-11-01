---
title: Upozornění linkerů LNK4221
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: b44ba8f0b88beda3e81d9baf59e5348ad4949b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460967"
---
# <a name="linker-tools-warning-lnk4221"></a>Upozornění linkerů LNK4221

Tento soubor objektu nedefinuje ještě definované veřejné symboly, takže se nepoužije žádná operace propojení, která tuto knihovnu užívá

Vezměte v úvahu následující fragmenty kódu dvě.

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}

```

Chcete-li zkompilovat soubory a vytvořte dva soubory objekt, spusťte **cl /c a.cpp b.cpp** z příkazového řádku. Pokud propojíte objektových souborů spuštěním **propojení/lib /out:test.lib a.obj b.obj**, zobrazí se upozornění LNK4221. Pokud jste se objekty spuštěním **propojení/lib /out:test.lib b.obj a.obj**, neobdržíte žádné upozornění.

Vzhledem k tomu, že má linker funguje způsobem poslední v první (ven LIFO), objeví se bez upozornění v druhém scénáři. V prvním případě b.obj se zpracovává před a.obj a a.obj nemá žádné nové symboly pro přidání. Tím, že linkeru, aby a.obj zpracovat jako první, se můžete vyhnout upozornění.

Běžnou příčinou této chyby je po dvou zdrojových souborů zadat možnost [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) se stejným názvem souboru záhlaví podle **předkompilovaných hlaviček** pole. Obvyklou příčinou tohoto problému se zabývá stdafx.h, protože ve výchozím nastavení, stdafx.cpp zahrnuje stdafx.h a nepřidá žádné nové symboly. Když jiný zdrojový soubor obsahuje stdafx.h s **/Yc** a při zpracování souboru .obj přidružené před stdafx.obj, linker vyvolá LNK4221.

Jeden ze způsobů, jak vyřešit tento problém se ujistěte, že pro každý předkompilované hlavičky, existuje pouze jeden zdrojový soubor, který ji obsahuje **/Yc**. Všechny ostatní soubory zdroje musí používat předkompilovaných hlaviček. Další informace o tom, jak toto nastavení změnit, naleznete v tématu [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md).