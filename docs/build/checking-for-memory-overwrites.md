---
title: Kontrola přepisů paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342254"
---
# <a name="checking-for-memory-overwrites"></a>Kontrola přepisů paměti

Pokud dojde k narušení přístupu při volání funkce manipulace s haldou, je možné, že váš program poškodil haldu. Běžným příznakem této situace by bylo:

```
Access Violation in _searchseg
```

Funkce [_heapchk](../c-runtime-library/reference/heapchk.md) je k dispozici v sestavení ladění i vydaných verzí (pouze systém Windows NT) pro ověření integrity haldy běhové knihovny. Můžete použít `_heapchk` podobným způsobem jako `AfxCheckMemory` funkce pro izolaci haldy, například:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Pokud tato funkce někdy neproběhne úspěšně, je nutné izolovat, v jakém okamžiku byla halda poškozena.

## <a name="see-also"></a>Viz také

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
