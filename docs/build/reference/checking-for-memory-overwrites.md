---
title: Kontrola přepisů paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: ff900c7366a28d19d3b90cbd4a6d9ee732e4ce02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621556"
---
# <a name="checking-for-memory-overwrites"></a>Kontrola přepisů paměti

Pokud dojde k narušení přístupu při volání funkce haldy manipulaci s je možné, že má váš program poškození haldy. Běžné příznakem této situaci by byl:

```
Access Violation in _searchseg
```

[_Heapchk –](../../c-runtime-library/reference/heapchk.md) funkce je k dispozici v obou ladění a verze sestavení (pouze Windows NT) pro ověřování integrity haldy knihovny běhu. Můžete použít `_heapchk` stejným způsobem jako `AfxCheckMemory` funkce haldy přepsat, izolovat například:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Pokud se tato funkce někdy nezdaří, je třeba izolovat v tomto okamžiku byla poškozena halda.

## <a name="see-also"></a>Viz také

[Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)