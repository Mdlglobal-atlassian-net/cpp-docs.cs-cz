---
title: Upozornění linkerů LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390357"
---
# <a name="linker-tools-warning-lnk4197"></a>Upozornění linkerů LNK4197

> Export '*exportname*"zadaný víc než jednou; použije se první specifikace

Export je zadán v několika a různými způsoby. Propojovací program použije první specifikace a zbytek ignoruje.

Pokud bude probíhat opětovné sestavení knihovny run-time jazyka C, můžete tuto zprávu ignorovat.

Pokud export je zadán více než jednou přesně stejným způsobem, nevydá linker upozornění.

Například následující obsah souboru .def by způsobilo toto upozornění:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Stejné export je zadána na příkazovém řádku (prostřednictvím exportu:) a v .def souboru.

2. Stejné export je uveden v souboru .def s rozdílnými atributy dvakrát.