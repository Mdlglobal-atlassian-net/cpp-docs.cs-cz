---
title: Upozornění linkerů LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 92702864a00455e4b70f00dfc9988bfb754e2e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183277"
---
# <a name="linker-tools-warning-lnk4197"></a>Upozornění linkerů LNK4197

> Export příkazu '*Export*' byl zadán několikrát. použití první specifikace

Export je zadán více a různými způsoby. Linker používá první specifikaci a ignoruje zbytek.

Při opětovném sestavování knihovny run-time jazyka C můžete tuto zprávu ignorovat.

Pokud je export zadán přesně stejným způsobem několikrát, linker nevydá upozornění.

Například následující obsah souboru. def by způsobil toto upozornění:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Stejný export se zadává na příkazovém řádku (prostřednictvím exportu:). a v souboru. def.

2. Stejný export je uveden dvakrát v souboru. def s různými atributy.
