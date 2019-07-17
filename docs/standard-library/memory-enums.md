---
title: '&lt;paměť&gt; výčty'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243852"
---
# <a name="ltmemorygt-enums"></a>&lt;paměť&gt; výčty

## <a name="pointer_safety"></a> pointer_safety – výčet

Výčet možných hodnot vrácených `get_pointer_safety`.

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>Poznámky

Rámci oboru **výčtu** definuje hodnoty, které může být vrácen `get_pointer_safety()`:

`relaxed` --odvozené neprovádí bezpečné (samozřejmě ukazatelů na objekty deklarované nebo bez přidělení) s ukazateli stejné jako ty bezpečně odvozené.

`preferred` – stejně jako předtím, ale neprovádí bezpečné odvozené ukazatele by neměla být dereferencována.

`strict` --odvozené neprovádí bezpečné ukazatele může být zpracovány jinak než tyto bezpečně odvozené.
