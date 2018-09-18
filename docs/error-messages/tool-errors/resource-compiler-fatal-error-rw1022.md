---
title: Závažná chyba kompilátoru prostředků RW1022 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caaefc045a31ca64aa9843927d550ef66285cb2e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099840"
---
# <a name="resource-compiler-fatal-error-rw1022"></a>Závažná chyba kompilátoru prostředků RW1022

**Vstupně-výstupní chyba zápisu do souboru**

Nástroj Resource Compiler nemůže zapisovat do souboru.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Nedostatek místa na disku. Volné místo se musí rovnat minimálně dvojnásobek velikosti spustitelného souboru, který vytváříte.

1. Svazek je jen pro čtení.

1. Chybné sektory.

1. Narušení sdílení.