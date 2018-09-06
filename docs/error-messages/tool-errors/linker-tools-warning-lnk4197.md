---
title: Upozornění Linkerů LNK4197 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4197
dev_langs:
- C++
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55044ce511e2584e2859b7e8a8d723cbe0976105
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894483"
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