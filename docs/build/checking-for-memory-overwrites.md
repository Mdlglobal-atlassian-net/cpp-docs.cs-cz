---
title: Kontrola přepisů paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823364"
---
# <a name="checking-for-memory-overwrites"></a>Kontrola přepisů paměti

Pokud dojde k narušení přístupu při volání funkce haldy manipulaci s je možné, že má váš program poškození haldy. Běžné příznakem této situaci by byl:

```
Access Violation in _searchseg
```

[_Heapchk –](../c-runtime-library/reference/heapchk.md) funkce je k dispozici v obou ladění a verze sestavení (pouze Windows NT) pro ověřování integrity haldy knihovny běhu. Můžete použít `_heapchk` stejným způsobem jako `AfxCheckMemory` funkce haldy přepsat, izolovat například:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Pokud se tato funkce někdy nezdaří, je třeba izolovat v tomto okamžiku byla poškozena halda.

## <a name="see-also"></a>Viz také:

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
