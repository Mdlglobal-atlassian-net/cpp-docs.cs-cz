---
title: Kontroluje se pro přepisy paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718639"
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